<template>
  <div class="bg-muted p-1.5 gap-1.5 size-20 justify-center rounded-lg flex flex-col items-center">
    <p
      class="text-highlighted rounded-sm bg-default size-full text-center flex items-center justify-center font-medium"
    >
      {{ value }}
    </p>
    <span class="text-toned text-xs -mt-1">{{ label }}</span>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  value: number | string;
  label: string;
}>();
</script>
