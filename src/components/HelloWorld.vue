<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Songs</h3>
    <ul>
      <li v-for="song in songs"
          :key="song.id">
          {{ song.title }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () { 
    return {
      songs: []
    }
  },
  async created(){
    console.log('creating');
    var foo = await axios.get('https://api.streamersonglist.com/v1/streamers/tylerlevsmusic/songs?');
    this.songs = foo.data.items;
    console.log(this.songs);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
a {
  color: #42b983;
}
</style>
