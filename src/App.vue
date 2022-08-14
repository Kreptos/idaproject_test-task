<template>
  <div class="header">
    <div class="add-product">Добавление товара</div>
    <!-- <div class="select"><select></select></div> -->
  </div>
  <div class="wrapper">
    <ProductAdd @addProductItem="add" />
    <div class="list-wrapper">
      <ProductItem 
        v-for="(item, index) in productData" 
        :data="productData[index]" 
        :index="index"
        @deleteProductItem="deleteItem(index)"/>
      </div>
  </div>
</template>

<script>
import ProductItem from './components/ProductItem.vue'
import ProductAdd from './components/ProductAdd.vue'
import ProductList from './components/ProductList.vue'

export default {
  name: 'App',
  components: {
    ProductItem,
    ProductAdd,
    ProductList,
  },
  data() {
    return {
      productData: [
      {
        name: 'Наименование товара',
        description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        imgUrl: 'https://cdnn21.img.ria.ru/images/148839/96/1488399659_0:0:960:960_600x0_80_0_1_e38b72053fffa5d3d7e82d2fe116f0b3.jpg',
        price: 10000,
      },
      {
        name: 'Наименование товара',
        description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        imgUrl: 'https://cdnn21.img.ria.ru/images/148839/96/1488399659_0:0:960:960_600x0_80_0_1_e38b72053fffa5d3d7e82d2fe116f0b3.jpg',
        price: 20000,
      },
      ],
    }
  },
  methods: {
    add(item){
      this.productData.push(item)
      console.log(item)
    },
    deleteItem(index){
      this.productData.splice(index, 1)
    }
  },  
}
</script>

<style>
body{
  background: #E5E5E5;
}
#app {
  color: #2c3e50;
  /* margin-top: 60px; */
  
}
.header{
  display: flex;
  justify-content: space-between;
  margin: 16px 32px 32px;
}
.add-product{
  font-weight: 600;
  font-size: 28px;
  line-height: 35px;
}
.wrapper{
  padding: 0 32px;
  display: flex;
  flex-wrap: wrap;
}
.list-wrapper{
    display: flex;
    flex-wrap: wrap;
    width: fit-content;
    max-width: calc(100vw - 396px);
    margin-left: 332px;
}
@media(max-width: 768px){
  .wrapper{
    flex-direction: column;
    padding: 0 16px;
  }
  .list-wrapper{
    margin-left: 0;
    max-width: 100%;
    flex-direction: column;
  }
}
</style>
