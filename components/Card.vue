<template>
    <div class="card">
        <button @click="deleteProduct_data(index)"><img src="./icons/Vector.svg"/></button>
        <img :src="product_data.link" alt=""/>
        <div class="product_name">{{product_data.name}}</div>
        <div class="product_description">{{product_data.description}}</div>
        <div class="product_price">{{product_data.price}} руб.</div>
    </div>
</template>


<script>
export default {
    props: {
        product_data: {
            type: Object,
            dafault() {
                return {}
            }
        },
        deleteProduct: {
            type: Function
        },
        index: {
            type: Number
        }
    }, 
     methods: {
         deleteProduct_data(index) {
            this.deleteProduct(index)
         }
     } 
}
</script>

<style lang="scss">
.card{
    position: relative;
    width: 332px;
    height: 423px;
    margin: 16px;
    gap: 8px;
    display: flex;
    flex-direction: column;
    background: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    img {
        width: 100%;
        height: 200px;
        border-radius: 4px 4px 0px 0px;
    }
    
    button {
    //    visibility: hidden;
       position:absolute;
       right: -10px;
       top: -10px;
       width: 32px;
       height: 32px; 
       background: #FF8484;
       box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
       border-radius: 10px;
       border: none;
       cursor: pointer;
       img {
        width: 12px;
        height: 16px;
       }
    }
    .card:hover button {
        visibility: visible;
    }
    .product_name {
        height: 25px;
        margin-left: 16px;
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 600;
        font-size: 20px;
        line-height: 25px;
        color: #3F3F3F;
    }
    .product_description {
        width: 300px;
        height: 80px;
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        margin-left: 16px;
        font-size: 16px;
        line-height: 20px;
        color: #3F3F3F;
    }
    .product_price {
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 600;
        margin: 16px 0 0 16px;
        font-size: 24px;
        line-height: 30px;
        color: #3F3F3F;
    }
}
</style>