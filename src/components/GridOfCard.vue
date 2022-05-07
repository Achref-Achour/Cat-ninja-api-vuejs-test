<script setup>
import Card from './Card.vue'

</script>
<template>
    <div class="container">
        <div class="row no-gutters">
            <div class="col-sm" v-for="item in breeds" >
                <Card :breed="item" />
            </div>
        </div>
    </div>
</template>



<script> 
import axios from 'axios'
export default {
    name: 'GridOfCard',
    components: {
        Card
    },
    data(){
        return{
            breeds:[]
        }
    },
    beforeCreate(){
      let config = {
        headers: {
            'Accept':'application/json'
        }
      }
      axios.get('https://catfact.ninja/breeds?limit=25',config).then(res=> 
      this.breeds = res.data.data
      )
    },
}
</script>