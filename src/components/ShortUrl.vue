<template>
  <div>
    <div>
    <form @submit.prevent="transform">
      <label for="textarea-input">Input text with Long URL Here:</label> <br />
      <div>
        <textarea v-model="urlText" id="urltext" rows="20" cols="70"></textarea>
      </div>
      <p>
        <button>Get text with the short version of URL</button>
      </p>
    </form>
  </div>

  <div></div>

  </div>
</template>


<script>
import Vue from 'vue';
import Resource from 'vue-resource';

Vue.use(Resource);

//our api endpoint to get shortened text + URL
const apiURL = 'https://e3hnfuqr03.execute-api.us-east-1.amazonaws.com/dev/url/shorten';

export default {
  name: 'ShortUrl',
  data: function () {
    return {
      id: null,
      response: null,
      urltext: []
    }
  },
  computed: {
    urlText: {
        get: function () {
          console.log(this.$refs.urltext);
        },
        set: function (newValue) {
          this.urltext += newValue;
      }
    }
  },
  methods: {
    urlText: function(event) {
      return this.value;
    },
    transform: function(event) {
        event.preventDefault();
        var payload = this.urlText;

        // send get request
        Vue.http.post(apiURL, payload).then(function(success) {
          console.log(success.message);
          this.urlText = success.message;
        }, function(error) {
          console.log(error);
        });
    }
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
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
