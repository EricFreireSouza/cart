<template>
  <nav class="nav has-shadow">
    <div class="nav-left">
      <router-link to="/" class="nav-item" title="Loja Online">
        LOJA ONLINE
      </router-link>
    </div>

    <!-- This "nav-toggle" hamburger menu is only visible on mobile -->
    <!-- You need JavaScript to toggle the "is-active" class on "nav-menu" -->
    <span v-b-toggle.collapse1 class="nav-toggle">
      <span></span>
      <span></span>
      <span></span>
    </span>

    <!-- This "nav-menu" is hidden on mobile -->
    <!-- Add the modifier "is-active" to display it on mobile -->
    <b-collapse id="collapse1" class="nav-right nav-menu mt-2 is-active">
    
      <router-link to="/" class="nav-item is-tab" exact-active-class="is-active" title="Loja">Loja</router-link>

      <div class="nav-item is-tab" :class="{ 'active-bottom-border': $route.path === '/cart' }">
        <div class="field is-grouped">
          <span class="control">
            <router-link to='/cart' class="btn btn-success navbar-btn" title="Carrinho">
              <!--span class="icon">
                <i class="fa fa-shopping-cart"></i>
              </span-->
              <span>Carrinho <span class="qtd">{{itemsInCart}}</span></span>
            </router-link>
          </span>
        </div>
      </div>
    
    </b-collapse>
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
.nav-toggle span {
  color: #fff;
}
.nav a {
  color: #fff;
}
.nav a:hover {
  color: #7a7a7a;
  text-decoration: none;
}
.nav-menu {
  background: #080808;
}
.nav-item a:not(.button).is-tab.is-active, 
.nav-item a:not(.button).is-tab:hover, 
a.nav-item:not(.button).is-tab.is-active,
a.nav-item:not(.button).is-tab:hover {
  border-bottom: 3px solid #ccc;
  color: #ccc;
  padding-bottom: calc(.75rem - 3px);
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
@media screen and (max-width: 768px){
  .nav-menu.nav-right {
    top: 51px;
    margin: 0 !important;
    border-top: 3px solid #ccc;
  }
}
@media screen and (min-width: 768px){
  .nav > .nav-menu.nav-right {
    text-align: right;
  }
  .nav > .nav-menu.nav-right.is-active.collapse:not(.show){
    display: block !important;
  }
  .nav > .nav-menu .nav-item.is-tab {
    display: inline-block;
  }
  .nav > .nav-menu a.nav-item:not(.button).is-tab.is-active {
    padding-bottom: calc(.75rem - -1px);
  }
}
</style>
