<template>
  <button :class="['btn', variant, { 'btn-full': full }]" 
    :type="type"
    @click="$emit('click', $event)">
    <slot />
  </button>
</template>

<script setup lang="ts">
defineProps({
  variant: {
    type: String,
    default: 'primary',
    validator: (value: string) => ['primary', 'secondary', 'outline', 'text'].includes(value)
  },
  type: {
    type: String,
    default: 'button'
  },
  full: {
    type: Boolean,
    default: false
  }
})

defineEmits(['click'])
</script>

<style scoped>
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.5rem 1rem;
  border-radius: 0.375rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s ease;
  border: none;
}

.primary {
  background-color: v-bind('appConfig.theme.colors.primary');
  color: white;
}

.primary:hover {
  filter: brightness(1.1);
}

.secondary {
  background-color: v-bind('appConfig.theme.colors.secondary');
  color: white;
}

.secondary:hover {
  filter: brightness(1.1);
}

.outline {
  background-color: transparent;
  border: 1px solid v-bind('appConfig.theme.colors.primary');
  color: v-bind('appConfig.theme.colors.primary');
}

.outline:hover {
  background-color: v-bind('appConfig.theme.colors.primary');
  color: white;
}

.text {
  background-color: transparent;
  color: v-bind('appConfig.theme.colors.primary');
  padding: 0.25rem 0.5rem;
}

.text:hover {
  text-decoration: underline;
}

.btn-full {
  width: 100%;
}
</style>

<script>
const appConfig = useAppConfig()
</script>
