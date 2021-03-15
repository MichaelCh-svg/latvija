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
          <div v-for="comment in comments" :key="comment.number">
            <hr>
            <p>{{comment.text}}</p>
            <p><i>-- {{comment.author}}</i></p>
          </div>
          <ul class='reviews'>
            <li>I've lived in Liepaja for 30 years, and I haven't even seen these places!
            <br/>-Roxanne
            </li>
            <!-- <li>I've lived in Liepaja for 3 years, and I've seen these places!
            <br/>-George
            </li> -->
            <li>I'm failing several classes.
            <br/>-Cloyde
            </li>
            <li>Great scenery! When my stimulus check comes in, I'll take a visit.
            <br/>-Sophrania
            </li>

          </ul>
        </div>

      </div>
      <div class='sum'>
        Capture your experiences before it's too late.

      </div>
      <div class='footer'>
        <div class='footer-item'>
          code:
          <a href="https://github.com/BYU-CS-260-Winter-2021/lab-1-photography-website-MichaelCh-svg.git"> git repository</a>
        </div>
      </div>
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
      comments: {
        number: 0,
        author: 'George',
        text: 'I\'ve lived in Liepaja for 3 years, and I\'ve seen these places!',
      },
      number: 1,
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
        
        this.comments.push({
          author: this.addedName,
          text: this.addedComment,
          number: this.number,
          // time: this.addedTime,
        });
        this.number += 1;
      },
    
  }
}
</script>
