<template>
    <div>
        <h1>Login</h1>
        <input v-model="username" type="text" placeholder="Username"><br><br>
        <input v-model="password" type="password" placeholder="Password"><br><br>
        <button @click="connect()">Connect</button>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name:'Login',
    data() {
        return {
        username: "",
        password: ""
    }
    },
    methods: {
        connect(){
            //  alert('username:' + this.username + ' password:' + this.password)
            const body = {
              username: this.username,
              password: this.password
          }
          
          axios.post('http://localhost:1407/login', body).then((res)=> {
              if (res.status === 2000 && res.data.success) {
                  //console.log(res.data.token);
                  localStorage.setItem('token', res.data.token); // clé , valeur 
                  this.$router.push('/') // pour etre redirigé vers home aprés le login
              }
          }).catch((err) => {
              alert('There is an error:')
          });
        }
    }
}
</script>
