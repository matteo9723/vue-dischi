<template>
 <div>
  <div v-if="loaded" class="main">
    <div class="cards">
      <div class="card" v-for=" ( item , index ) in characters" :key= "index.author">
        <div class="character"  >
          <img :src=item.poster alt="">
        </div>
        <div class="description">
          <h3>{{item.title}}</h3>
          <h5>{{item.author}}</h5>
          <h6>{{item.year}}</h6>
        </div>
      </div>
    </div>  
  </div>   
  <div v-else class="loader"> <h1>caricamento....</h1> </div> 
 </div> 
  
</template>

<script>

import axios from 'axios';


export default {
  name:'Main',

  data(){
    return{
      characters:[],
      loaded:false,
      apiUrl:'https://flynn.boolean.careers/exercises/api/array/music'
    }
  },
  methods:{
    getApi(){
      axios.get(this.apiUrl)
        .then( r => {
          this.characters = r.data.response;
          console.log(r.data.response);
          this.loaded = true;
        })
        .catch( e => {
          console.log(e);
        })
    }
  },
  mounted(){
    this.getApi();
  }
}

</script>

<style lang="scss" scoped>
.main{
  background-color: #1D2C3A;
  height: calc(100vh - 40px);
  .cards{
  display: flex;
  align-content: center;
  flex-wrap: wrap;
  width: 60%;
  height: 100%;
  margin: 0 auto;
  .card{
    width: calc(100% / 5 - 20px);
    padding: 10px;
    border: 1px solid black;
    background-color:rgba($color: #a79c9c, $alpha: .5) ;
    margin: 5px 10px;
    .character{
      width: 100%;
      display: flex;
      justify-content: center;
      margin-bottom: 20px ;
      img{
        width: 8vw;
        height: 8vw;
      };
    };
    .description{
      h3{
        text-align: center;
        color: white;
      };
      h5{
        text-align: center;
        color: rgb(179, 175, 175);
      };
      h6{
        text-align: center;
        color: rgb(179, 175, 175);
      };
    };
  };
 };
};

.loader{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
};

  
  
</style>