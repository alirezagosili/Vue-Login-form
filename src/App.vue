<script setup>
import { ref } from 'vue';

const username = ref('');
const password = ref('');
const message = ref('');
const buttonText = ref('Login');

const users = [
  { username: 'user1', password: 'pass1' },
  { username: 'user2', password: 'pass2' },
  { username: 'user3', password: 'pass3' },
  { username: 'user4', password: 'pass4' },
  { username: 'user5', password: 'pass5' },
];

const login = () => {
  const user = users.find(users => users.username === username.value);
  
  if (!user) {
    message.value = 'This username does not exist';
    return;
  }
  
  if (user.password === password.value) {
    buttonText.value = 'Login Success';
    message.value = '';
  } else {
    message.value = 'Wrong password';
  }
};
</script>
<template>
  <main class="container">
    <div class="login-form">
      <h1>Welcome Back</h1>
      <p>Please Enter Your Details</p>
      <form action="">
        <div class="input-field">
          <label for="username">Username</label>
          <input type="text" id="username" v-model="username" placeholder="Enter Your Username">
        </div>
        <div class="input-field">
          <label for="password">Password</label>
          <input type="password" id="password" v-model="password" placeholder="Enter Your Password">
        </div>
        <div class="rules">
          <div>
            <input type="checkbox">
            <span>Remember me</span>
          </div>
          <a href="#">Forget Your Password?</a>
        </div>
        <button type="button" @click="login">{{ buttonText }}</button>
      </form>
      <p>{{ message }}</p>
      <p>Don't have an account? <a href="#">Register here</a></p>
      <div class="user-list">
        <h2>Available Users:</h2>
        <ul>
          <li>
             username: user1, password: pass1
          </li>
          <li>
             username: user2, password: pass2
          </li>
          <li>
             username: user3, password: pass3
          </li>
          <li>
             username: user4, password: pass4
          </li>
          <li>
             username: user5, password: pass5
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>
<style>
:root{
    --text-black: #000000;
    --text-lighter: #a3a3a3;
    --white:#ffffff;
    --backdrop:rgba(255, 255, 255, 0.05);
    --font-primary: 'Roboto', sans-serif;
}
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
a{
    text-decoration: none;
    color: var(--white);
}
body{
    font-family: var(--font-primary);
    background-image: url(../src/assets/images/bg.png);
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    overflow: hidden;
}
.container{
    display: grid;
    position: relative;
}

.container::before{
    position: absolute;
    content: "";
    width: 100%;
    height: 100%;
    backdrop-filter: blur(5px);
    background-color: var(--backdrop);
    grid-column: 1/2;
    z-index: -1;
}

.login-form{
    min-height: 100vh;
    width: 100%;
    max-width: 450px;
    margin-inline: auto;
    padding: 1rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.login-form h1{
    color: var(--white);
    font-weight: 500;
    font-size: 2.75rem;
    margin-bottom: 1rem;
    text-align: center;
}

.login-form p{
    color: var(--text-black);
    font-weight: 500;
    font-size: 1.2rem;
    text-align: center;
    margin-bottom: 2rem;
}

.login-form form{
    display: grid;
    gap: 2rem;
}
.input-field{
    display: grid;
    gap: 5px;
}

.input-field label{
    font-size: 1.2rem;
    font-weight: 500;
    color: var(--white);
}

.input-field input{
    padding: 0.75rem 0;
    outline: none;
    border: none;
    background-color: transparent;
    border-bottom: 1px solid var(--text-lighter);
    color: var(--white);
}
.input-field input::placeholder{
    font-size: 1rem;
    color: var(--text-lighter);
}
.rules{
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
}
.rules div span {
    color: var(--text-lighter);
}
.login-form button{
    margin-bottom: 2rem ;
    padding: 1rem;
    outline: none;
    border: none;
    font-size: 1rem;
    color: var(--white);
    background-color: var(--text-black);
    border-radius: 5px;
    cursor: pointer;
    transition: all 0.3s ease-in-out;
}
.login-form button:hover{
    color: var(--text-black);
    background-color: var(--text-lighter);
}
.user-list {
  margin-top: 1rem;
  padding: 1rem;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 5px;
}

.user-list h2 {
  color: var(--text-black);
  font-size: 1.2rem;
  margin-bottom: 1rem;
}

.user-list ul {
  list-style-type: none;
  padding: 0;
}

.user-list li {
  color: var(--text-black);
  margin-bottom: 0.5rem;
}

@media screen and (width > 768px) {
    .container{
        grid-template-columns: 
        minmax(0, 1fr)
        minmax(0, calc(1600px/ 2))
        minmax(0, calc(1600px/ 2))
        minmax(0, 1fr);
    }
    .container::before{
        grid-column: 3/5;
        border-left: 1px solid var(--text-lighter);
    }

    .login-form{
        grid-column: 3/4;
    }
    
}
</style>