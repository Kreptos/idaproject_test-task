<template>
  <div class="product-add">
    <form ref='form' @submit.prevent='createProductItem'>
      <label for="">Наименование товара <span>*</span></label>
      <input v-model="item.name" name="name" type="text" placeholder="Введите наименование товара">

      <label for="">Описание товара</label>
      <textarea v-model="item.description" name="description" placeholder="Введите описание товара"></textarea>
      
      <label for="">Ссылка на изображение товара <span>*</span></label>
      <input v-model="item.imgUrl" name="imgUrl" type="text" placeholder="Введите ссылку">

      <label for="">Цена товара <span>*</span></label>
      <input v-model="item.price" name="price" type="text" placeholder="Введите цену">
      
      <button @click="$emit('addProductItem', this.item)" :disabled="!form">Добавить товар</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'ProductAdd',
  props: {
    data: Object
  },
  data(){
    return {
      item: {
        name: '',
        description: '',
        imgUrl: '',
        price: '',
      },
      form: false,
      name: false,
      imgUrl: false,
      price: false,
    }
  },
  watch: {
    'item.name': function(){
      this.name = this.item.name ? true : false
      this.checkForm()
    },
    'item.imgUrl': function(){
      this.imgUrl = this.item.imgUrl ? true : false
      this.checkForm()
    },
    'item.price': function(){
      this.price = this.item.price ? true : false
      this.checkForm()
    }
    
  },
  methods:{
    checkForm(){
      if(this.name && this.imgUrl && this.price) this.form = true
      else this.form = false
    },
    createProductItem(submitEvent){
      let data = submitEvent.target.elements
      let f = false
      let newItem = {
        name: data.name.value,
        description: data.description.value,
        imgUrl: data.imgUrl.value,
        price: data.price.value,
      }

      Object.keys(newItem).forEach(function(key){
        f = this[key] ? true : false
      }, newItem)
      
      console.log(f)

      this.item = newItem

      this.item = {
        name: '',
        description: '',
        imgUrl: '',
        price: '',
      }
    }
  }

}
</script>

<style>
.product-add{
  width: 284px;
  /* width: 15%; */
  height: 392px;
  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  padding: 24px;
  justify-content: space-around;
  position: fixed;
  z-index: 3;
  left: 32px;
}
.product-add form{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
}
label{
  font-weight: 400;
  font-size: 10px;
  line-height: 13px;
  letter-spacing: -0.02em;
  color: #49485E;
}
label span{
  color: #FF8484;
}
input, textarea{
  padding: 10px 16px;
  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;
  resize: none;
}
textarea{
  height: 88px;
}
input::placeholder, textarea::placeholder{
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
  text-align: left;
  color: #B4B4B4;
}

button{
  border-radius: 10px;
  background: #7BAE73;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  text-align: center;
  letter-spacing: -0.02em;
  color: #FFFFFF;
  padding: 10px 0;
  border: none;
  cursor: pointer;
}
button:hover{
  background: #6c9e65;
}
button:active{
  background: #61925b;
}
button:disabled{
  background: #eee;
  color: #B4B4B4;
  cursor: default;
}
@media(max-width: 768px){
  .product-add{
    position: inherit;
    margin-bottom: 16px;
    width: auto;
  }
}
</style>
