<template>
<select class="select" v-model="sorting" size="1">
    <option  selected >По умолчанию</option>
    <option>Сначала дешевле</option>
    <option>Сначала дороже</option>
</select>
</template>


<script>
export default {
    data () {
  return {
    sorting: 'По умолчанию'
  }
},
    props: {
        sortingProduct: { 
            type: Function
        },
    },
    methods: {
        // sortingProductInSelect(sorting) {
        // this.sortingProduct(sorting)
        // }
    sortingProductInSelect () {
        this.$emit('sortingProduct', {
            sorting: this.sorting
        })
  }
    }
}

</script>


<style lang="scss">
.select {
 outline: none;
 width: 140px;
 height: 36px; 
 margin-right: 32px;  
 background: #FFFEFB;
 border: none;
 box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
 border-radius: 4px;
}


</style>