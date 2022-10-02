<script setup>
const name = "";
const password = "";

function checkUser() {
  if (this.name != "admin" && !this.password != "admin") {
    alert("Wrong info");
  } else {
    document.getElementById("login").click();
  }
}
</script>
<template>
  <div class="container">
    <div class="form-container">
      <h2>Please Login to our service</h2>
      <h3>Default Username and Password is: admin</h3>
      <div class="form">
        <p>Username</p>
        <input type="text" v-model="name" placeholder="admin" />
      </div>
      <div class="form">
        <p>Password</p>
        <input type="password" v-model="password" placeholder="admin" />
      </div>
      <div class="btn-group">
        <button @click="checkUser()">Log in</button>
        <a href="#">Forgot Password</a>
        <router-link to="/dashboard" id="login"> </router-link>
      </div>
    </div>
  </div>
</template>
<style scoped>
input {
  padding: 10px;
}

button {
  padding: 0.5rem;
  background: transparent;
}

a {
  color: black;
  text-decoration: none;
}

.contianer {
  position: relative;
}

.form-container {
  border: 1px solid black;
  width: fit-content;
  height: fit-content;
  padding: 30px;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form {
  margin: 5px;
}

.btn-group {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.btn-group > * {
  margin: 5px;
}
</style>
