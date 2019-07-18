<template>
    <div class="login">
        <h3>SIgn In</h3>
        <input type="text" v-model="email" name="email" placeholder="Email"><br>
        <input type="password" v-model="password" name="password" placeholder="Password"><br>
        <button @click="login">Connection</button>
        <p>You dont have an account? You can <router-link to="/sign-up"> create one</router-link></p>
    </div>
</template>

<script>
import firebase from 'firebase'

export default {
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    login: function () {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password).then(
        function (user) {
          alert('Welldone ! You are now connected')
        },
        function (err) {
          alert('Ooops. ' + err.message)
        }
      )
    }
  }
}
</script>

<style scoped>
.login {
    margin-top: 40px;
}
input {
    margin: 10px 0;
    width: 20%;
    padding: 15px;
}
button {
    margin-top: 20px;
    width: 10%;
    cursor: pointer;
}
p {
    margin-top: 40px;
    font-size: 13px;
}
p a {
    text-decoration: underline;
    cursor: pointer;
}
</style>
