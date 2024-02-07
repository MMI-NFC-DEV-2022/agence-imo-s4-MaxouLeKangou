<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
    import AfficheMaison from '../../../components/AfficheMaison.vue'
    import { type SchemaOffreMaison } from '../../../types';
    import { ref } from "vue";

    

    const houses = ref<SchemaOffreMaison>({
            nomMaison: 'New_Caledonia',
            prix: 250000,
            favori: false,
            image: '/img/house.png',
            nbrChambres: 2,
            nbrSDB: 1,
            adresse: '2 rue André Boulloche, 25200 Montbéliard',
            surface: '150m²',
        });
        

</script>

<template>
    <RouterLink :to="'offres/' + houses.nomMaison">
        <AfficheMaison v-bind="houses"  />
    </RouterLink>
</template>