<script setup lang="ts">
import Title from '@/components/Title.vue';

</script>

<template>
  <div id="app">
    <Title />
    <!-- Any global navigation headers can go here -->
    
    <!-- Vue Router will swap Home or Login right here -->
    <router-view />
  </div>
</template>