<template>
  <div class="flex items-center gap-2 p-2 px-3 border border-muted rounded-lg">
    <span v-if="icon" class="p-1.5 size-fit rounded-lg flex" :class="iconClass">
      <UIcon :name="icon" size="1.5rem" />
    </span>
    <div class="flex flex-col">
      <p class="text-muted text-xs">{{ title }}</p>
      <p class="text-toned font-medium">{{ description }}</p>
    </div>
  </div>
</template>

<script lang="ts" setup>
const {
  title = "Default",
  description = "No description available",
  iconClass = "text-primary bg-primary/15",
} = defineProps<{
  title: string;
  description: string;
  icon?: string;
  iconClass?: string;
}>();
</script>
