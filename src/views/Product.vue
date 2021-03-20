<template>
<div>
  <div class="info">
            <h1>{{ product.name }}</h1>
          </div>
  <div class="image">
    <img :src="'/images/'+product.image">
  </div>
  <div class = "description">
    <p>Author's note: {{product.description}}</p>
     </div>
  <div class = 'comments'>
          <h2>visiter comments</h2>
          <form v-on:submit.prevent="addComment(product)">
            <input v-model="addedName" placeholder="Name">
            <textarea v-model="addedComment"></textarea>
            <br />
            <button type="submit">Comment</button>
          </form>
          <h3>Comments</h3>
          <div v-for="comment in product.comments" :key="comment.number">
            <hr>
            <p>{{comment.text}}</p>
            <p><i>-- {{comment.author}}</i></p>
            <form v-on:submit.prevent="settrue(comment)">
            <button type="submit"> edit</button>
            </form>
            <form v-on:submit.prevent="del(comment)">
            <button type="submit"> delete</button>
            </form>
            <div v-if='comment.editing===true'>
              <form v-on:submit.prevent="edit(comment)">
            <input v-model="comment.author">
            <textarea v-model="comment.text"></textarea>
            <br />
            <button type="submit">Finish edit</button>
          </form>
        </div>
            
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
    addComment(product) {
        console.log("comment, method called");
        product.comments.push({
          author: this.addedName,
          text: this.addedComment,
          number: this.number,
          editing: false,
        });
        this.number += 1;
        this.addedComment = '';
        this.addedName = '';
      },
      settrue(comment){
        comment.editing = true;
      },
      edit(comment){
        comment.editing=false;
      },
      del(comment) {
        // let object = this.comments.reduce(erase=>erase.number=comment.number);
        let index = this.product.comments.indexOf(comment);
        this.product.comments.splice(index, 1);
      }
    
  }
}
</script>

<style scoped>
.comments{
  background-color:darkgoldenrod;
  padding-top: 20px;
  padding-bottom: 20px;
}
.intro {
  font-style: italic;
}
.info {
  /* background: #000000; */
  color: #000;
  padding: 10px 30px;
  height: 40px;
  margin-bottom:10px;
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