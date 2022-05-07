
<template>
    <div class="flip-card" >
        <div class="flip-card-inner">
            <div class="flip-card-front">
                <p><b>{{ breed.breed }}</b></p>
                <p>Country : {{ breed.country }}<br>
                Origin : {{ breed.origin }}<br>
                Coat : {{ breed.coat }}<br>
                Pattern : {{ breed.pattern }}</p>
            
            </div>
            <div class="flip-card-back">
                <p>{{fact}}</p>
            </div>
        </div>
    </div>
</template>


<style scoped>
.flip-card {
  background-color: transparent;
  width: 300px;
  height: 250px;
  border: 1px solid  #00000073;
  border-radius: 10px;
  margin : 3px;
  padding: 10px
}


.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}


.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; 
  backface-visibility: hidden;
}


.flip-card-front {
  background-color: #fff;
  color: black;
  border-radius: 10px;

}

.flip-card-back {
  background-color: #fff;
  color: black;
  border-radius: 10px;

  transform: rotateY(180deg);
}
</style>

<script> 
import axios from 'axios';
export default {
    name:'Card',
    props:{
        breed: {}
    },
    data(){
        return{
            fact:''
        }
    },
    beforeCreate(){
        let config = {
                headers: {
                    'Accept':'application/json'
                }
            }
            axios.get('https://catfact.ninja/fact',config).then(res=>
            this.fact = res.data.fact
            )
    },
}
</script>