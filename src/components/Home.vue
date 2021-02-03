<template>
  <div>
    <h1 class="display-3 font-weight-light mb-4">Negocie e Consulte suas Ações</h1>
    <v-sheet :elevation="6" class="pa-2 primary mb-2">
      <v-icon class="white--text mr-3 mb-1">I</v-icon>
      <span class="headline white--text font-weight-light">Voce pode salvar & carregar seus dados</span>
    </v-sheet>
     <v-sheet :elevation="6" class="pa-2 success darken-1">
      <v-icon class="white--text mr-3 mb-1">I</v-icon>
      <span class="headline white--text font-weight-light">Clique em 'Finalizar Dia' para inicias um nov dia</span>
    </v-sheet>
    <v-divider class="my-4" />
      <p class="display-1"><strong>Seu Saldo: </strong>{{ funds | currency}}</p>
  </div>
</template>

<script>
import currency from "@/filters/currencies";
export default {
  filters: { currency },
  computed: {
    funds() {
      return this.$store.getters.funds;
    },
  },
};
</script>

<style>
</style>
