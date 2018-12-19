<template>
  <div class="hello">
    <button @click="login">login</button>
  </div>
</template>

<script>
import firebase from 'firebase'

// コンソールから取得したコンフィグをペースト
// Initialize Firebase
var config = {
  apiKey: 'AIzaSyC_yoWZfT-XHZda_PAuyIA-witVkbxjihU',
  authDomain: 'auth-vue-sample.firebaseapp.com',
  databaseURL: 'https://auth-vue-sample.firebaseio.com',
  projectId: 'auth-vue-sample',
  storageBucket: 'auth-vue-sample.appspot.com',
  messagingSenderId: '1011538488281'
}
firebase.initializeApp(config)

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js PWA'
    }
  },
  methods: {
    login () {
      const provider = new firebase.auth.GoogleAuthProvider()
      firebase.auth().signInWithPopup(provider)
        .catch(error => alert(error.message))
        .then(data => {
          // ここにログインできたときの処理を書く
          alert('login success')
          console.log(data)
        })
    }
  }
}
</script>
