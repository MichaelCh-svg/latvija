<template>
  <div class="home">
    <h1>Latvia</h1>
    <div class='content'>
        <img class ='lat' src="/images/lat8.jpg"/>
        <div>
          I served a christian mission in Latvia. This photo is taken from a bridge
          in Liepaja, Latvia's 3rd largest city.
          Latvia is located in Eastern Europe. It gained it's independence from
          the USSR in 1991. Less than 2 million people live in the country.
          Most inhabitants speak latvian or russian, and a large portion are
          trilingual, speaking latvian, russian, and english.
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Home',
  components: {
    
  }
}
</script>

<style scoped>
*{
  margin: 20px;
}
.content{
  background-color:darkgoldenrod;
  margin: 0 auto;
  padding:10px;
  align-self:center;
}
.lat{
  
  margin: 0px auto;

}
img{
  width: 85%;
  max-width: 360px;
  /* padding: 25px; */
  /* border-style:solid; */
}

h1{
  text-decoration:underline;
}

@media only screen and (min-width: 700px) {
  .content {
    display: flex;
    flex-direction:row;
  }
  img, .lat{
  width: 300px;
  height: 0%;
}
}
</style>


