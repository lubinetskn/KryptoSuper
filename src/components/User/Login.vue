<template>
  <div class="login">
    <h3>Вход</h3>
    <input type="text" v-model="email" placeholder="Email"><br>
    <input type="password" v-model="password" @keyup.enter="signIn" placeholder="Пароль"><br>
 
    <v-btn large v-on:click="signIn" class="cyan">Войти</v-btn>
  </div>
</template>

<script>
  import firebase from 'firebase'

  export default {
    data: function () {
      return {
        email: '',
        password: ''
      }
    },
    methods: {
      signIn: function () {
        firebase.auth().signInWithEmailAndPassword(this.email, this.password).then(
          (user) => {
            this.$router.replace('hello')
          },
          (err) => {
            alert('Oops. ' + err.message)
          }
        )
      }
    }
  }
</script>

<style scoped>  /* "scoped" attribute limit the CSS to this component only */
  .login {
    margin: 40px auto;
    text-align: center;
  }
  input {
    margin: 10px 0;
    padding: 15px;
    width: 100%;
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
