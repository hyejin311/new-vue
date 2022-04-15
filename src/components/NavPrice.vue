<template>
<div id="header">
 <h3>제품카테고리</h3>
  <dl>
  <dt>구매상품 총</dt>
  <dd>{{(cartTotal)}} 원 </dd>
  <dd><button @click="displayCart = !displayCart">장바구니보기 {{cart.length}}</button>
  <ul v-if="displayCart">
  <li v-for="(item,index) in cart" :key="index">{{item.name}} : {{item.price}}원
  </li>
  </ul>
  </dd>
  </dl>
</div>
</template>

<script>
export default {
props:['cart'],
data(){
    return {
      displayCart:false
    }
},
computed:{
    cartTotal(){
    return this.cart.reduce( (inc, item) => Number(item.price) + inc, 0 )
  }
}
}
</script>

<style scoped>
h3{
  font-size:30px;
  color:#666;
}
header>dl{
  display:flex;
  justify-content: flex-end;
  align-items: center;
}
header dl>dd>ul{
  position:absolute;
  right:0;
  top:50px;
  z-index:100;
  padding:5px 10px;
  border:1px solid #666;
  background-color:#fff;
}
header dl>dd>ul>li{
  padding: 10px 0;
  border-bottom:1px solid #666;
}
header dl>dd>ul>li:last-child{
  border-bottom:none;
}
</style>