<template>
<div>
  <div class="image">
    <img :src="'/images/'+product.image">
  </div>
  <div class = 'comments'>
          <form v-on:submit.prevent="addComment()">
            <input v-model="addedName" placeholder="Name">
            <textarea v-model="addedComment"></textarea>
            <br />
            <button type="submit">Comment</button>
          </form>
          <h3>Comments</h3>
          <div v-for="comment in this.comments" :key="comment.number">
            <hr>
            <p>{{comment.text}}</p>
            <p><i>-- {{comment.author}}</i></p>
          </div>
        </div>
</div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      random: 0,
      amount: 0,
      product: {},
      comments: [],
      number: 1,
      addedName: '',
      addedComment: '',
    }
  },
  created() {
    this.product = this.$root.$data.products.find(product => product.id === parseInt(this.$route.params.id));
    this.random =
      Math.floor(Math.random() * 90) + 10;
    // this.amount = this.random * parseFloat(this.product.price.replace(/\$|,/g, ''));
    this.amount = this.amount.toFixed(2);
  },
  methods: {
    addComment() {
        console.log("comment, method called");
        this.comments.push({
          author: this.addedName,
          text: this.addedComment,
          number: this.number,
        });
        this.number += 1;
      },
    
  }
}
</script>

<style scoped>
.comments{
  background-color:darkgoldenrod;
  padding-top: 20px;
}
.intro {
  font-style: italic;
}
.products {
  display: flex;
  flex-wrap: wrap;
}
.products img {
  border: 1px solid #333;
  height: 50px;
  width: 40px;
  margin-left: 10px;
  object-fit: cover;
}
textarea {
    width: 100%;
    max-width: 500px;
    height: 100px;
}
form{
  margin-top: 20px;
  display:flex;
  flex-wrap: wrap;
  flex-direction:column;
  align-items: center;
}
button, input {
  width: 160px;
}
</style>