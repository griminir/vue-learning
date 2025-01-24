<script setup>
import { defineProps } from 'vue';

defineProps({
  bg: {
    type: String,
    default: 'bg-gray-100',
  }
});
</script>

<template>
  <!-- remember backticks so you can type in js -->
  <div :class="`${bg} p-6 rounded-lg shadow-md`">
    <!-- slot is same as children in react -->
    <slot></slot>
  </div>
</template>
