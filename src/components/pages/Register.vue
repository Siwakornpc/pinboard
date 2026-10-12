<script setup lang="ts">
import { ref } from 'vue';
import { supabase } from '@/lib/supabase';

const name = ref('');
const email = ref('');
const password = ref('');

const loading = ref(false);
const errorMessage = ref('');
const successMessage = ref('');

async function register() {
    loading.value = true;
    errorMessage.value = '';
    successMessage.value = '';

    try {
        const { data, error } = await supabase.auth.signUp({
            email: email.value,
            password: password.value,
            options: {
                data: {
                    name: name.value,
                },
            },
        });

        if (error) throw error;

        successMessage.value = 'Registration successful! Check your email if confirmation is required.';
    } catch (error: unknown) {
        errorMessage.value = error instanceof Error ? error.message : 'Something went wrong.';
    } finally {
        loading.value = false;
    }
}

</script>

<template>
    <!-- the main box -->
    <div class="box">
        <h3 :style="{ color: 'white', textAlign: 'center' }">Register</h3>
    
        <form @submit.prevent="register">
            <!-- name -->
            <label :style="{
                color: 'white',
            }" for="name">Name</label>
            <input
                v-model="name"
                type="text"
                name="name"
                id="name" placeholder="My name"
                required
            >

            <!-- email -->
            <label :style="{
                color: 'white',
            }" for="email">E-mail</label>
            <input
                v-model="email"
                type="email"
                name="email"
                id="email" placeholder="yourname@email.com"
                required
            >

            <!-- password -->
            <label :style="{
                color: 'white',
            }" for="password">Password</label>
            <input
                v-model="password"
                type="password"
                name="password"
                id="password"
                autocomplete="new-password"
                minlength="6"
                required
            >

            <p v-if="errorMessage" class="error">
                {{ errorMessage }}
            </p>

            <p v-if="successMessage" class="success">
                {{ successMessage }}
            </p>

            <p> </p>

            <div class="flex">
                <button type="submit" :disabled="loading">
                    {{ loading
                        ? 'Registering...'
                        : 'Register'
                    }}
                </button>
            </div>
        </form>

        <p> </p>
    </div>
</template>

<style scoped>
::placeholder {
    color: #ffffff40;
    transition: 0.2s ease;
}
input:hover::placeholder {
    color: #ffffff80;
}
input:focus::placeholder {
    color: #ffffff00;
}

label {
    display: block;
    margin-block-start: 0.5em;
    margin-block-end: 0.5em;
}

.error {
    font-weight: bold;
    color: #fa938c;
}

.success {
    font-weight: bold;
    color: #79f883;
}
</style>