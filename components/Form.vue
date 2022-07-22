<template>
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
                <input
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
</template>

<script>
export default {

    data() {

        return {
           name: '',
           link: '',
           price: '',
           description: '',
        }
    },

    computed: {

        isFormValid() {
            if((this.name !== '') && (this.link !== '') && (this.price !== '')) {
              return true
            }
        },

        isNameError() {
            return this.name == '' 
        },

        isLinkError() {
            return this.link == '' 
        },

        isPriceError() {
            return this.price == '' 
        },
    },
    
    methods: {
        validate() {
           if(!this.isFormValid) {
            return
           }
           alert('Форма отправлена')
        }
    }
}
</script>

<style lang="scss">
.form {
padding: 24px;
max-width: 332px;
height: 440px;
display: flex;
flex-direction: column;
align-items: center;
gap: 16px;
margin-left: 32px;
margin-top: 16px;
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
color: #B4B4B4;
border-radius: 4px;
border: none;

}
.description {
    height: 108px;
}
button {
margin-top: 8px;
width: 284px;
height: 36px;
border-radius: 10px;
border: none;
}
}
</style>