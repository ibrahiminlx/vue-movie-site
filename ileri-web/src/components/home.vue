<template>
  <div class="home">
<!--    <h1>{{title}}</h1>-->
    <h5>{{data.data.data.opening[0].emsVersionId}}</h5>
<!--    <h5>{{data.data.data.newsStories.length}}</h5>-->
<!--    <h5>{{data.data.data.newsStories[0]}}</h5>-->
<!--    <h5>{{data.data.data.newsStories[0].title}}</h5>-->
<!--    <h5>{{data.data.data.newsStories[0].link}}</h5>-->
    <h1>Abc-film</h1>
    <div class="row">
      <div class="col-md-4 col-lg4" v-for="(data,index) in data.data.data.opening" :key="index">
        <img :src="data.posterImage.url" class="img-fluid">
        <h3 @click="goTodetail(data.emsVersionId)" class="mt-2">{{data.name}}</h3>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'


const options = {
  method: 'GET',
  url: 'https://flixster.p.rapidapi.com/movies/get-opening',
  params: {countryId: 'usa'},
  headers: {
    'X-RapidAPI-Key': '29e5c17275mshc405a3ab6085034p10d53djsn0266442dc3d9',
    'X-RapidAPI-Host': 'flixster.p.rapidapi.com'
  }
};


const api='https://jsonplaceholder.typicode.com/users'

export default {
  name: 'home',
  props:{
    id:String
  },
  data () {
    return {
      title: 'Home',

      products:[
      {
        productTitle:"ABCN",
        image       : require('../assets/images/product1.png'),
        productId:1
      },
      {
        productTitle:"KARMA",
        image       : require('../assets/images/product2.png'),
        productId:2
      },
      {
        productTitle:"Tino",
        image       : require('../assets/images/product3.png'),
        productId:3
      },
      {
        productTitle:"EFG",
        image       : require('../assets/images/product4.png'),
        productId:4
      },
      {
        productTitle:"MLI",
        image       : require('../assets/images/product5.png'),
        productId:5
      },
      {
        productTitle:"Banans",
        image       : require('../assets/images/product6.png'),
        productId:6
      }
      ],
      data:[],
      test:''

    }
  },
  methods:{
  goTodetail(prodId) {
    let proId=prodId
    this.$router.push({name:'details',params:{Pid:proId}})
    this.$props.id=proId
  },
  },

  mounted() {
    axios
      .request(options)
      .then(response => (this.data = response))
  },

}
</script>

<style scoped>
.row img{
  max-height: 31em;
  width: 100%;

}
.row h3{
  cursor:pointer;
}
</style>
