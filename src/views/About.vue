<template>
  <div class="about">
    <h1>About</h1>
    <div class='content'>
          <img class ='lat' src="/images/lat5.jpg"/>
          <div>
            This is chemps. I'm currently studying computer science.
            Some of the photos I take seem unusual to take, but I like
            them since they still capture some of the feel of the place
            that otherwise gets lost. Click the portfolio tab to see some
            of these photos.
          </div>
    </div>
      
  </div>
</template>

<style scoped>
*{
  margin: 20px;
}
.lat{
  width:100%;
  margin: 0 auto;
}
/* .about, content{
  border-style:solid;
} */
h1{
  text-decoration:underline;
}
.about{
  align-items:center;
}
.content{
  align-self: center;
  background-color:darkgoldenrod;
  /* display: flex; */
  
  /* justify-content:center; */
  align-content: center;
  align-items: center;
  /* width: 90%; */
  margin: 0 auto;
  padding: 15px;
  
}
img{
  width: 90%;
  max-width: 360px;
  border-style:solid;
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