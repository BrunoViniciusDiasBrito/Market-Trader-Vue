<template>
  <v-flex class="pr-3 pb-3" xs12 md6 lg4>
    <v-card class="green darken-3 white--text">
      <v-card-title class="headline">
        <strong>{{ stock.name }} <small>(Preço: {{ stock.price | currency }})</small></strong>
      </v-card-title>
    </v-card>
    <v-card>
      <v-container fill-height>
        <v-text-field 
        :error="insufficientFunds  || quantity < 0 || !Number.isInteger(quantity)"
        label="Quantidade" 
        type="number" 
        v-model.number="quantity"></v-text-field>
        <v-btn 
        class="green darken-3 white--text" 
        @click="buyStock"
        :disabled="insufficientFunds  || quantity <= 0 || !Number.isInteger(quantity)">{{ insufficientFunds ? 'Insuficiente' : 'Comprar' }}</v-btn>
      </v-container>
    </v-card>
  </v-flex>
</template>

<script>
import verifyFunds from "@/mixins/fundsVerify";
import currency from "@/filters/currencies";
export default {
  filters: { currency },
  props: ["stock"],
  data() {
    return {
      quantity: 0,
    };
  },
  mixins: [verifyFunds],
  methods: {
    buyStock() {
      const order = {
        stockId: this.stock.id,
        quantity: this.quantity,
        stockPrice: this.stock.price,
      };

      this.$store.dispatch("buyStock", order);
      this.quantity = 0;
    },
  },
};
</script>

<style>
</style>
