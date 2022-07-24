<template>
<section class="generalSection">
<div class="header">
    <h3>Добавление товара</h3>
    <Select 
    :sortingProduct="sortingProduct"
    :sorting="sorting"
    />
</div>
    <div class="wrapper">
      <form @submit.prevent="validate()">
        <div class="form">
            <div>
                <p>Наименование товара</p>
                <input
                    type="text"
                    v-model="name"
                    :class="{error: isNameError}"
                    placeholder="Введите наименование товара"
                /> 
                <p class="errorText" v-if="isNameError">Поле является обязательным</p>
            </div>
            <div>
                <p>Описание товара</p>
                <textarea
                    class="description" 
                    type="text" 
                    v-model="description"
                    placeholder="Введите описание товара"
                />
            </div>
            <div>
                <p>Ссылка на изображение товара</p>
                <input 
                    type="text" 
                    v-model="link" 
                    :class="{error: isLinkError}"
                    placeholder="Введите ссылку"
                />
                <p class="errorText" v-if="isLinkError">Поле является обязательным</p>
            </div>
            <div>
                <p>Цена товара</p>
                <input
                    type="text" 
                    v-model="price"
                    :class="{error: isPriceError}"
                    placeholder="Введите цену"
                /> 
                <p class="errorText" v-if="isPriceError">Поле является обязательным</p>
            </div>
            <button :disabled="!isFormValid" type="submit">Добавить товар</button>
        </div>
    </form>
    <div class="cardList">
        <Card 
            v-for="(product, index) in productList"
            :key="index"
            :index="index"
            :product_data="product"
            :deleteProduct="deleteProduct"
        />
    </div>  
    </div>
</section> 
</template>

<script>
import Card from './Card.vue'
import Select from './Select.vue';
export default {
    data() {
        return {
            name: "",
            link: "",
            price: "",
            description: "",
            productList: [],
        };
    },
    computed: {
        isFormValid() {
            if ((this.name !== "") && (this.link !== "") && (this.price !== "")) {
                return true;
            }
        },
        isNameError() {
            return this.name == "";
        },
        isLinkError() {
            return this.link == "";
        },
        isPriceError() {
            return this.price == "";
        },
    },
    methods: {
            deleteProduct(index) {
                this.productList.splice(index, 1)
            },
            sortingProduct(data) {
                 if(data === 'Сначала дешевле') {
                    this.productList.sort((a,b) => a.price - b.price)
                 }
                 if(data === 'Сначала дороже') {
                    this.productList.sort((a,b) => b.price - a.price)
                 }
                 if(data === 'По умолчанию') {
                    this.productList
                 }
            },
        validate() {
            if (!this.isFormValid) {
                return;
            }
            this.productList = [...this.productList, { name: this.name,
                                                       description: this.description, 
                                                       link: this.link, 
                                                       price: this.price}
                                ]
           
        },
        
    },
    components: { Card, Select }
}
</script>

<style lang="scss">
@import url("https://use.typekit.net/nbh0lcy.css");
body {
  font-family: source-sans-pro, sans-serif;  
  background: #E5E5E5;
}
.wrapper {
    display: flex;
}
.header {
    font-weight: 600;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;

    h3 {
       height: 35px;
       margin-top: 32px;
       margin-left: 32px;
       font-weight: 600;
       font-style: normal;
       font-size: 28px;
       line-height: 35px;
    }
}
.generalSection {
    display: flex;
    flex-direction: column;
}
.cardList {
    display: flex;
    flex-wrap: wrap;
}
.form {
    position: sticky;
padding: 24px;
max-width: 332px;
height: 440px;
display: flex;
flex-direction: column;
align-items: center;
gap: 10px;
margin-left: 32px;
margin-top: 16px;
margin-right: 8px;
background: #FFFEFB;
box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
border-radius: 4px;
.error {
    border: 1px solid #FF8484;
}
.errorText {
    margin-top: 4px;
    color: #FF8484;
    font-family: 'Source Sans Pro';
    font-style: normal;
    font-weight: 400;
    font-size: 8px;
    line-height: 10px;
}
p {
height: 13px;
margin: 0 0 4px 0;
font-family: 'Source Sans Pro';
font-style: normal;
font-weight: 400;
font-size: 10px;
line-height: 13px;
color: #49485E;
letter-spacing: -0.02em;
}
input {
outline: none;
width: 284px;
height: 36px;
padding-left: 16px;
background: #FFFEFB;
box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
border-radius: 4px;
border: none;
position: relative;
}
::placeholder {
 position: absolute;
 top: 10px;
 color: #B4B4B4;
 
}
input:focus {
    border: 1px solid #58c3f5;
}
textarea {
    outline: none;
    width: 284px;
    height: 108px;
    padding-left: 16px;
    background: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    border: none;
    resize: none;
}
textarea:focus {
    border: 1px solid #58c3f5;
}
button {
background: #7BAE73;
margin-top: 8px;
width: 284px;
height: 36px;
border-radius: 10px;
border: none;
color: #FFFFFF;
cursor: pointer;
}
button:disabled {
    cursor: default;
    background: #EEEEEE;
    color: #B4B4B4;
}
}
</style>