<template>
  <nav class="nav has-shadow">
    <div class="nav-left">
      <router-link to="/" class="nav-item">
        LOJA ONLINE
      </router-link>
    </div>

    <!-- This "nav-toggle" hamburger menu is only visible on mobile -->
    <!-- You need JavaScript to toggle the "is-active" class on "nav-menu" -->
    <span class="nav-toggle">
      <span></span>
      <span></span>
      <span></span>
    </span>

    <!-- This "nav-menu" is hidden on mobile -->
    <!-- Add the modifier "is-active" to display it on mobile -->
    <div class="nav-right nav-menu">
      <router-link to="/" class="nav-item is-tab" exact-active-class="is-active">Loja</router-link>

      <div class="nav-item is-tab" :class="{ 'active-bottom-border': $route.path === '/cart' }">
        <div class="field is-grouped">
          <span class="control">
            <router-link to='/cart' class="btn btn-success navbar-btn">
              <!--span class="icon">
                <i class="fa fa-shopping-cart"></i>
              </span-->
              <span>Carrinho <span class="qtd">{{itemsInCart}}</span></span>
            </router-link>
          </span>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  computed: {
    itemsInCart(){
      let cart = this.$store.getters.cartProducts;
      return cart.reduce((accum, item) => accum + item.quantity, 0)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.nav {
  background: #080808;
  height: auto;
  margin-bottom: 2rem;
}
.nav a {
  color: #fff;
}
.nav-item a:not(.button).is-tab.is-active, a.nav-item:not(.button).is-tab.is-active {
  border-bottom: 3px solid #ccc;
  color: #ccc;
}
.control .btn, .control .btn:hover { 
  color: #fff;
}
.qtd {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  color: #6c757d;
  text-align: center;
  white-space: nowrap;
  vertical-align: middle;
  background-color: #fff;
  border-radius: 10px;
  line-height: 1;
}
</style>
