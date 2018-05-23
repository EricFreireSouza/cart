<template>
  <div class="cart">
    <div v-show="products.length">
      <h1 class="title">Carrinho de Compras</h1>
      
      <table class="table is-striped">
      	<thead>
      		<tr>
      			<th>Produto</th>
            <th>Preço</th>
      			<th>Quantidade</th>
      			<th>Subtotal</th>
      			<th>Remover</th>
      		</tr>
      	</thead>
      	<tbody>
      		<tr v-for="p in products">
        		<td>{{ p.name }}</td>
            <td>R$ {{ p.price }}</td>
        		<td>{{ p.quantity }}</td>
        		<td>R$ {{ p.quantity * p.price }}</td>
        		<th><button @click='removeToCart(p)' class='btn btn-danger btn-sm'>X</button></th>
        	</tr>
        </tbody>
        <tfoot>
        	<tr>
        		<td><b>Total:</b></td>
        		<td></td>
        		<td></td>
        		<td><b>R$ {{ total }}</b></td>
        		<th><button v-show="products.length" class='btn btn-warning is-primary' @click='checkout'>Finalizar</button></th>
        	</tr>
        </tfoot>
      </table>
    </div>
    
    <div v-show="!products.length">
      <h1 class="title">Carrinho vazio!</h1>
      <p><router-link to="/"><em>Ir as compras</em></router-link></p>      
    </div>
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
    }
  },
  methods: {
  	...mapActions([
      'removeToCart'
    ]),
  	checkout(){
  	  alert('Valor total R$ ' + this.total)
  	}
  }
}
</script>