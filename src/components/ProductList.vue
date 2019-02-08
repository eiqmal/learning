<template>
  <div>
    <h1>Product List</h1>
    <ul>
      <li v-for="product in products"> {{product.title}} - {{product.price}}</li>
    </ul>
  </div>
</template>

<script>
  import shop from '@/api/shop'
  import store from '@/store/index'

    export default {
      computed: {
          products ()
          {
              return store.state.products
          }
      },
      created () {
          // this getProducts here refer to method inside ./api/shop file
        shop.getProducts(products => {
          //assign the variable from data() took from ./api/shop file
          // this.products = products

          //commit the mutation
          store.commit('setProducts', products)
        })
      }
    }
</script>

<style scoped>

</style>
