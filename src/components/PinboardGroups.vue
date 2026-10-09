<script setup lang="ts">
import { ref } from "vue";

const time = ref(new Date);

const thisTime = ref(time.value.toLocaleTimeString());
</script>

<template>
    <div class="box">
        <div class="plank flex"
        :style="{
            color: 'white',
            gap: '2px',
        }">
            <div class="l flex"
            :style="{
                padding: '0 8px',
            }">
                <p>{{ thisTime }}</p>
            </div>
            <div class="m"
            :style="{
                display: 'flex',
                flexDirection: 'column',
                justifyContent: 'center',
                alignItems: 'left',
            }">
                <h2>Meet us!</h2>
                <span>test</span>
            </div>
        </div>
    </div>
</template>

<style>
.plank {
    border: 1px solid #e3cfca20;
    transition: 0.2s ease;
}

.plank:hover {
    background-color: #ffd7cc60;
    border: 1px solid #e6bbae80;
    color: #f7e1c1;
    cursor: pointer;
    box-shadow: 0px 10px 20px #00000040;
}

.plank:active {
    background-color: #b3978f20;
    border: 1px solid #dbb9af20;
    color: #f7e1c1;
    cursor: pointer;
    box-shadow: 0px 2px 5px #00000050;
    transition: 0s ease;
}
</style>