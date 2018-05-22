<template>
  <div class="cart">
    <h1 class="title">Carrinho de Compras</h1>
    <p v-show="!products.length">
    	<i>Your cart is empty!</i>
    	<router-link to="/">Go shopping</router-link>
    </p>
    <table class="table is-striped" v-show="products.length">
    	<thead>
    		<tr>
    			<th>Nome</th>
    			<th>Quantidade</th>
    			<th>Preço unitário</th>
    			<th>Subtotal</th>
    			<th>Remover</th>
    		</tr>
    	</thead>
    	<tbody>
    		<tr v-for="p in products">
        		<td>{{ p.name }}</td>
        		<td>{{ p.quantity }}</td>
        		<td>R$ {{ p.price }}</td>
        		<td>R$ {{ subTotal }}</td>
        		<th><button @click='removeToCart(products)' class='button is-info'>X</button></th>
        	</tr>
        	<tr>
        		<td><b>Total:</b></td>
        		<td></td>
        		<td></td>
        		<td><b>R$ {{ total }}</b></td>
        		<th></th>
        	</tr>
    	</tbody>

    </table>
    <p><button v-show="products.length" class='button is-primary' @click='checkout'>Finalizar</button></p>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  computed: {
    ...mapGetters({
      products: 'cartProducts'
    }),
    total () {
      return this.products.reduce((total, p) => {
        return total + p.price * p.quantity
      }, 0)
    },
    subTotal () {
    	return this.products.reduce((subTotal, p) => {
          return subTotal = p.quantity * p.price
      	}, 0)
    }
  },
  methods: {
  	...mapActions([
      'removeToCart'
    ]),
  	checkout(){
  	  alert('Pay us $' + this.total)
  	}
  }
}
</script>