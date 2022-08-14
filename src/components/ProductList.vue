<template>
    <div class="list-wrapper">
        <ProductItem 
        v-for="(item, index) in data" 
        :data="data[index]" 
        :index="index"
        @deleteProductItem="$emit('deleteProductItem')(index)"/>
    </div>
</template>

<script>
import ProductItem from './ProductItem.vue'

export default {
    name: 'ProductList',
    components: {
        ProductItem,
    },    
    props: {
        data: Array
    },
    data() {
        return {
        // productData: [
        // {
        //     name: 'Наименование товара',
        //     description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        //     imgUrl: 'https://cdnn21.img.ria.ru/images/148839/96/1488399659_0:0:960:960_600x0_80_0_1_e38b72053fffa5d3d7e82d2fe116f0b3.jpg',
        //     price: 10000,
        // },
        // {
        //     name: 'Наименование товара',
        //     description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        //     imgUrl: 'https://cdnn21.img.ria.ru/images/148839/96/1488399659_0:0:960:960_600x0_80_0_1_e38b72053fffa5d3d7e82d2fe116f0b3.jpg',
        //     price: 20000,
        // },
        // ],
        // newData: {
        //     name: 'Наименование товара',
        //     description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        //     imgUrl: 'https://cdnn21.img.ria.ru/images/148839/96/1488399659_0:0:960:960_600x0_80_0_1_e38b72053fffa5d3d7e82d2fe116f0b3.jpg',
        //     price: 30000,
        // }
        }
    },
}
</script>

<style scoped>

</style>
