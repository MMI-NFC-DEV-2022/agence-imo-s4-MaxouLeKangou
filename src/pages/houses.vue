<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
    import { ref, onMounted } from "vue";
    import AfficheMaison from '@/components/AfficheMaison.vue'

    import { createClient } from '@supabase/supabase-js'

    const houses = ref()

    const supabaseUrl = import.meta.env.VITE_SUPABASE_URL
    const supabaseAnonKey = import.meta.env.VITE_SUPABASE_KEY

    const supabase = createClient(supabaseUrl, supabaseAnonKey)

    async function getHouses() {
        try {
            const { data } = await supabase.from('house').select()
            houses.value = data
        } catch (error) {
            console.log(error)
        }
    }

    onMounted(() => {
        getHouses()
    })

</script>

<template>
    <RouterLink v-for="house in houses" :key="house.id" :to="'offres/' + house.id">
        <AfficheMaison v-bind="house"  />
    </RouterLink>
</template>