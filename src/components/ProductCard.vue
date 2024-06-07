<template>
  <Card>
    <template #title>
      {{ product.producto }}
    </template>
    <template #content>

      <p><strong>Antigüedad:</strong> {{ product.antiguedad }} años</p>
      <p><strong>Cantidad mínima:</strong> {{ product.cantidad_minima }} costales</p>
      <p><strong>Cantidad máxima:</strong> {{ product.cantidad_maxima }} costales</p>
      <p><strong>Número de ventas:</strong> {{ product.numero_ventas }}</p>
    </template>
    <template #footer>

      <Button label="Generar pedido" icon="pi pi-shopping-cart" class="mr-2 custom-button" @click="generateOrder" />
      <Button label="Agregar a favoritos" icon="pi pi-star" class="mr-2 custom-button" @click="addToFavorites" />
      <Button label="No recomendar" icon="pi pi-ban" class="custom-button" @click="doNotRecommend" />
    </template>
  </Card>
</template>

<script>
import Card from 'primevue/card';
import Button from 'primevue/button';

export default {
  name: 'ProductCard',
  components: {
    Card,
    Button
  },
  props: {
    product: Object
  },
  methods: {
    generateOrder() {
      this.$router.push({ name: 'TheGenerateOrder', params: { productId: this.product.id } });
    },
    addToFavorites() {
      alert(`${this.product.producto} agregado a favoritos`);
    },
    doNotRecommend() {
      alert(`No recomendar ${this.product.producto}`);
    }
  }
}
</script>

<style scoped>

.p-card-footer .p-button {
  margin-right: 8px;
}


.p-card-content p strong {
  font-weight: bold;
}

.custom-button {
  background-color: #22c55e!important;
  border-color: #22c55e !important;
  color: #fff !important;
}
</style>
