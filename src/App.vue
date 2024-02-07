<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { createClient } from '@supabase/supabase-js'

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_KEY

const supabase = createClient(supabaseUrl, supabaseAnonKey)

async function signInWithGithub() {
    const { data, error } = await supabase.auth.signInWithOAuth({
        provider: 'github',
    })
}


async function upsertMaison(dataForm, node) {
 const { data, error } = await supabase.from("Maison").upsert(dataForm);
 if (error) node.setErrors([error.message])
}


</script>

<template>
  <main style="background-color: #FFEFD7; height: 100vh;">
    <header>
      <h1>Test</h1>
      <nav class="*:text-red-500 flex flex-col">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/houses">Houses</RouterLink>
      </nav>
    </header>
    <button type="button" @click="signInWithGithub()">GITHUB</button>
    <button type="button" @click="upsertMaison()">ADD DATA</button>
    <Suspence>
      <RouterView />
    </Suspence>

    <footer style="background-color: #0C6704; height: 200px; position: absolute; bottom: 0; width: 100vw;">
      <p style="color: white;">Bonjour le monde</p>
    </footer>
  </main>
</template>
