<template>
  <!-- regiter with name -->
  <div class="hello">
    <!--
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="http://chat.vuejs.org/" target="_blank" rel="noopener">Vue Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="http://vuejs-templates.github.io/webpack/" target="_blank" rel="noopener">Docs for This Template</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
    -->

    <p> My event </p>

    <fb-signin-button :params="fbSignInParams" @success="onSignInSuccess" @error="onSignInError">
      Sign in with Facebook
    </fb-signin-button>

    <p id="event"> </p>
    <p id="event1"> </p>
    <p id="event2"> </p>
    <p id="event3"> </p>
    <p id="event4"> </p>
    <p id="event5"> </p>
    <p id="event6"> </p>


  </div>
</template>

<!-- scope like token in facebook -->
<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to My Vue.js PWA',
      fbSignInParams: {
        scope: 'email,user_likes',
        return_scopes: true
      }
    }
  },
  methods: {
    onSignInSuccess (response) {
      // graph api in Facebook
      window.FB.api('/me/events', text => {
        // getdata in array[0] and getarrayinJSON
        console.log(`Good to see you, ${text.data[0]['name']}`)
        var s = `${text.data[0]['name']}`
        var s1 = `${text.data[0]['description']}`
        var s2 = `${text.data[0]['start_time']}`
        var s3 = `${text.data[0]['end_time']}`
        var s4 = `${text.data[0]['place']['name']}`
        var s5 = `${text.data[0]['place']['location']['latitude']}`
        var s6 = `${text.data[0]['place']['location']['longitude']}`
        document.getElementById('event').innerHTML = s
        document.getElementById('event1').innerHTML = s1
        document.getElementById('event2').innerHTML = s2
        document.getElementById('event3').innerHTML = s3
        document.getElementById('event4').innerHTML = s4
        document.getElementById('event5').innerHTML = s5
        document.getElementById('event6').innerHTML = s6
      })
    },
    onSignInError (error) {
      console.log('OH NO', error)
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  h1,
  h2 {
    font-weight: normal;
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
    color: #35495E;
  }
  
  .fb-signin-button {
    /* This is where you control how the button looks. Be creative! */
    display: inline-block;
    padding: 4px 8px;
    border-radius: 3px;
    background-color: #4267b2;
    color: #fff;
  }
</style>