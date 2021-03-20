<template>
  <div class='page'>
      <h1>Reviews</h1>
      <div class='content'>
        <img class ='lat-rev' src="/images/lat11.jpg"/>
        <div>
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
            <form v-on:submit.prevent="del(comment)">
            <button type="submit"> delete</button>
            </form>
          </div>
        </div>

      </div>
      
      <!-- <div class='footer'>
        <div class='footer-item'>
          code: 
          <a href="https://github.com/BYU-CS-260-Winter-2021/lab-1-photography-website-MichaelCh-svg.git"> git repository</a>
        </div>
      </div> -->
    </div>
</template>

<script>
export default {
  name: "Review",
  components: {
    
  },
  data() {
    return {
      searchText: "",
      comments: [],
      number: 0,
      addedName: '',
      addedComment: '',
      
    };
  },
  computed: {
    
  },
  methods: {
    addComment() {
        // let c = moment().format('MMMM Do YYYY, h:mm:ss a');
        // this.addedTime = c;
        // if (!(this.number in this.comments))
        //   Vue.set(app.comments, this.number, new Array);
        // this.addedName = addedName;
        // this.addedComment = addedComment;
        console.log("comment, method called");
        this.comments.push({
          author: this.addedName,
          text: this.addedComment,
          number: this.number,
          // time: this.addedTime,
        });
        this.number += 1;
      },
      del(comment) {
        // let object = this.comments.reduce(erase=>erase.number=comment.number);
        let index = this.comments.indexOf(comment);
        this.comments.splice(index, 1);
      }
    
  }
}
</script>

<style scoped>
.content{
  background-color:darkgoldenrod;
  padding: 30px;
}
img{
  width: 100%;
  width:350px;
}
h1{
  text-decoration-line:underline;
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
