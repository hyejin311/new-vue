<template>
<figure>
<img :src="item.image" :alt="item.name" />
<figcaption>
<dl>
<dt>{{item.name}}</dt>
<dd>{{item.description}}</dd>
<dd>레벨</dd>
<dd>{{item.price}} 원</dd>
</dl>
</figcaption>
</figure>
<!-- plus -->
<p>
<button @click="$emit('addToCart',item)">+</button>
</p>
</template>

<script>
export default {
props:{
 item:{
   type:Object
 } 
},
emits:['addToCart'],
components:{}
}
</script>

<style scoped>
p{
  width:100px;
  display:flex;
  justify-content: center;
  align-items: center;
}
figure{
  width:800px;
  display:flex;
  flex-wrap:wrap;
  justify-content: space-between;
  align-content: flex-start;
}
figure>img{
  width:150px;
}
figure>figcaption{
  width:500px;
}
</style>