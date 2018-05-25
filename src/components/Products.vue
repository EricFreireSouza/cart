<template>
  <b-container fluid>
    <h1 class="title">Todos os Livros</h1>
    <p>Total de Livros: {{length}}</p>
    <b-row class="product"> 
      <b-col md="4" v-for="product in products" track-by="id">
        <b-card-group deck class="prodts">
          <b-card tag="article" style="max-width: 100%;" class="mb-4">
            <h2>{{product.name}}</h2>
            <b-media> 	
              <b-img slot="aside" :src=product.thumb alt="left image" />
              <p class="mb-0">{{product.description}}</p>
              <span class="price">R$ {{product.price}}</span>
            </b-media>
            <b-button @click='addToCart(product)' class='btn btn-success' title="Adicionar ao carrinho">Adicionar ao carrinho</b-button>
          </b-card>
        </b-card-group> 
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  name: 'Products',
  computed: mapGetters({
    products: 'allProducts',
    length: 'getNumberOfProducts'
  }),
  methods: mapActions([
    'addToCart'
  ])
}
</script>

<style>
</style>