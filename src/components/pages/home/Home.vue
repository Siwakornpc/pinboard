<script setup lang="ts">
import PinboardGroups from '@/components/PinboardGroups.vue';
</script>

<template>
    <h1
        class="head1"
        :style="{ textAlign: 'center', color: 'white' }"
    >Pinboard</h1>
    
    <div class="box">
        <p :style="{ color: 'white' }">Welcome to Pinboard!</p>
    </div>

    <PinboardGroups>
        
    </PinboardGroups>
</template>

<style scoped>

</style>
