<template>
<NavPrice :cart="cart" />

<!-- box 상품선택 -->
  <div id="box">
    <ul class="form">
      <li>
        <span>
          <label for="userMax">최고값</label>
          <input id="userMax" v-model="max" readonly />
        </span>
        <span>
         선택상품 갯수: {{filteredProducts.length}}
        </span>
      </li>
      <li>
        <input type="range" min="0" step="1000" max="30000" v-model="max" />
      </li>
      <li>
        <input type="checkbox" id="userLabel" v-model="displayLabel" />
        <label for="userLabel">레벨보기</label>
      </li>
    </ul>
    <!-- 제품카테고리 -->
     <ul class="list">
       <li v-for="(item,index) in filteredProducts"
       :key="index">
       <ProductItem :item="item" :cart="cart" @addToCart="addToCart" />
       </li>
     </ul>
  </div>
</template>

<script>
import ProData from '@/assets/data.json'
import NavPrice from '@/components/NavPrice.vue'
import ProductItem from '@/components/ProductItem.vue' 
export default {
data(){
    return {
      displayCart:false,
      cart:[],
      displayLabel:true,
      max:20000,
      products:ProData
    }
  },
  components:{
    ProductItem,NavPrice
  }
  ,
 computed:{
  filteredProducts(){
    return this.products.filter(item => (item.price < this.max));
  },
  cartTotal(){
    return this.cart.reduce( (inc, item) => Number(item.price) + inc, 0 )
  }

},
 methods:{
   addToCart(product){
     this.cart.push(product);
   }
 }
}
</script>

<style scoped>

</style>