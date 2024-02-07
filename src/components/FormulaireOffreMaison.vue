<script setup lang="ts">
import { ref } from "vue";
import AfficheMaison from "./AfficheMaison.vue";
// On fait une variable réactive qui référence les données
// ATTENTION : faire une Ref pas une Reactive car :
// c'est l'objet qui doit être réactif, pas ses props
const maison = ref({});

</script>
<template>
  <div>
    <div class="p-2">
      <h2 class="text-2xl">Résultat (Prévisualisation)</h2>
      <!-- Optionnel on affiche les données -->
      <AfficheMaison v-bind="maison" />
    </div>

    <div class="p-2">
      <!-- On passe la "ref" à FormKit -->
      <FormKit type="form" v-model="maison">
        <FormKit name="nom" label="nom" />
        <FormKit name="prix" label="prix" type="number" />
        <FormKit name="favori" label="mettre en valeur" type="checkbox" />
      </FormKit>
    </div>
  </div>
</template>
