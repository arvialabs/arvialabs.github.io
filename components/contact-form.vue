<template>
  <form @submit="onSubmit" class="flex flex-col gap-2 max-w-sm">
    <FormField v-slot="{ componentField }" name="email">
      <FormItem>
        <FormLabel class="text-background text-base"
          >Email <span class="text-destructive">*</span></FormLabel
        >
        <FormControl>
          <Input
            type="text"
            class="bg-background rounded-none"
            placeholder="Your email"
            v-bind="componentField"
          />
        </FormControl>
        <FormDescription>
          Don&rsquo;t worry, we&rsquo;ll never spam you.
        </FormDescription>
        <FormMessage class="text-xs" />
      </FormItem>
    </FormField>
    <FormField v-slot="{ componentField }" name="message">
      <FormItem>
        <FormLabel class="text-background text-base">Message</FormLabel>
        <FormControl>
          <Textarea
            class="bg-background rounded-none"
            placeholder="Your message"
            v-bind="componentField"
          />
        </FormControl>
        <FormDescription>
          Please briefly describe your use case. We&rsquo;ll get back to you
          with details on how we can onboard you.
        </FormDescription>
        <FormMessage class="text-xs" />
      </FormItem>
    </FormField>
    <BrandConcentric variant="secondary" class="w-[250px]">
      <Button
        variant="secondary"
        type="submit"
        class="w-full mt-5 border border-primary p-6 rounded-none cursor-pointer"
      >
        Submit
      </Button>
    </BrandConcentric>
    <p v-if="errorMessage" class="text-destructive text-sm">
      {{ errorMessage }}
    </p>
  </form>
</template>

<script setup lang="ts">
import {
  FormControl,
  FormDescription,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { toast } from "vue-sonner";
import { toTypedSchema } from "@vee-validate/zod";
import { useForm } from "vee-validate";
import * as z from "zod";

const ACCESS_KEY = "1c3cec64-4bf2-45b3-870b-24f505ba32cb";
const FORM_URL = "https://api.web3forms.com/submit";

const schema = toTypedSchema(
  z.object({
    email: z.string().email(),
    message: z.string(),
  }),
);
const form = useForm({ validationSchema: schema });
const errorMessage = ref("");

const onSubmit = form.handleSubmit(async (values) => {
  const payload = {
    ...values,
    access_key: ACCESS_KEY,
  };

  try {
    const response = await fetch(FORM_URL, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(payload),
    });

    if (!response.ok) {
      throw new Error("Failed to submit the form");
    }

    const data = await response.json();
    if (!data.success) {
      throw new Error("Failed to submit the form");
    }

    toast.success("Thanks for reaching out!", {
      description: "We will get back to you as soon as possible.",
    });
    form.resetForm();
    errorMessage.value = "";
  } catch (error) {
    errorMessage.value = "An error occurred while submitting the form.";
  }
});
</script>
