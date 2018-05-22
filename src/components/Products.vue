<template>
	<b-container>
		<h1 class="title">Todos os Livros</h1>
    	<p>Total de Livros: {{length}}</p>
		<b-row class="product">
			<b-card-group deck class="prodts">
	    		<b-card tag="article" style="max-width: 100%;" class="mb-2" v-for="product in products" track-by="id">
		          	<h2>{{product.name}}</h2>
		          	<b-row>
			          	<b-col>
					        <b-img left :src=product.thumb alt="left image" />
						    <p class="card-text">{{product.description}}</p>
						    <span class="price">R$ {{product.price}}</span>
					    </b-col>
				    </b-row>
				    <b-button @click='addToCart(product)' class='button is-info'>Adicionar ao carrinho</b-button>
			  	</b-card>
		  	</b-card-group>

	    	<!--table class="table is-striped">
			    <thead>
			      <tr>
			        <th>Nome</th>
			        <th>Descrição</th>
			        <th>Preço</th>
			        <th></th>
			      </tr>
			    </thead>
			    <tbody>
			      <tr v-for="product in products" track-by="id">
			        <td>{{product.name}}</td>
			        <td>{{product.description}}</td>
			        <td>${{product.price}}</td>
			        <td><button @click='addToCart(product)' class='button is-info'>Adicionar ao carrinho</button></td>
			      </tr>
			    </tbody>
			</table-->
		</b-row>
	</b-container>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  name: 'app',
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