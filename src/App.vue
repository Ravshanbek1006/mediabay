<template>
  <div class="container">
    <h1>Рекомендуемое</h1>
    <div class="rec">
      <a href="" class="rec-a"  v-for="(channel , index ) in recChannal" :key="index">
       <div class="rec-img" > <img :src="channel.picture" alt=""> </div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      recChannal:[],
    }
  },
  methods:{
    getChannels(){
      fetch('https://api.mediabay.uz/v2/videos/movies?order=recommend&page=1&size=15')
      .then(res=>{res.json().then(res2=>{
        this.recChannal = res2.data
        
      })
      })
    }
  },
  mounted() {
    this.getChannels()
  },

  computed:{

  }



};
</script>

<style>
body {
  background-color: rgb(119, 119, 119);
  color: #fff;
}
.container {
  margin: 80px;
}
.rec{
  display: flex;
  flex-wrap: wrap;
}
.rec-a {
  display: flex;
  flex-direction: column;
  align-items: center;
}
a {
  display: flex;
  flex-wrap: wrap;
  text-decoration: none;
  color: #fff;
  margin: 10px;
   transition: all 0.5s ease;
   padding: 10px;
   margin-bottom: 20px;
}
a span {
  font-size: 20px;
  color: #fff;
}
.span-box{
  width: 200px;
  padding: 10px 0;
 text-align:center;
}
.rec-img {
  width: 200px;
  height: 355px;
   transition: all 0.5s ease;
}

a:hover{
  color: red !important;
  transform: scale(1.05);
  background-color: #555;
  border-radius: 8px;
}
img{
  width: 100%;
  object-fit: cover;
}
</style>
