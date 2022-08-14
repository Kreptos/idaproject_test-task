<template>
  <div class="product-card">
    <div class="product-img"><img :src='data.imgUrl'></div>
    <div class="product-description">
      <div class="product-title">{{data.name}}</div>
      <div class="product-text">{{data.description}}</div>
      <div class="product-price">{{data.price}} руб.</div>
    </div>
    <div class="product-delete" @click="$emit('deleteProductItem'), index"><img src="../assets/delete.svg"></div>
  </div>
</template>

<script>
export default {
  name: 'ProductItem',
  props: {
    data: Object,
    index: Number,
  },

}
</script>

<style scoped>
  img{
    width: 100%;
    /* height: 100%; */
    /* left:  */
  }
  .product-card{
    position: relative;
    max-width: 332px;
    min-height: 423px;
    display: flex;
    flex-direction: column;
    background: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    margin: 16px;
    margin-right: 0;
    margin-top: 0;
    cursor: pointer;
  }
  .product-img{
    overflow: hidden;
    /* width: 50%; */
    max-height: 200px;
  }
  .product-description{
    height: 183px;
    padding: 16px 16px 24px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }
  .product-title{
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;
  }
  .product-text{
    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
  }
  .product-price{
    font-weight: 600;
    font-size: 24px;
    line-height: 30px;
  }
  .product-delete{
    position: absolute;
    display: none;
    width: 32px;
    height: 32px;
    right: -8px;
    top: -8px;
  }
  .product-card:hover .product-delete{
    display: block;
  }
  @media(max-width: 768px){
    .product-card{
      margin-left: 0;
      max-width: none;
    }
  }
</style>
