<template>
 <div>
  <Header/>
   <Form/> 
 </div>
</template>

<script>
import Header from '../components/Header.vue';
import Form from '../components/Form.vue';

export default {

    data() {

    },
    name: "IndexPage",
    components: { Header, Form },
}
</script>
