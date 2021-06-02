<template>
  <div class="nav-borders">
    <nav class="wrapper">
      <router-link to="/"
        ><img
          src="https://i.pinimg.com/originals/8d/c5/31/8dc531fd1168a51c9e5bc9aca0d45051.jpg"
          alt="logo"
      /></router-link>

      <div>
        <router-link to="/favourites" alt="Favourites" v-if="isLoggedIn">&#10084;</router-link>
        <router-link to="/">Home</router-link>
        <router-link to="/add" v-if="isLoggedIn">Add recipe</router-link>
        <router-link to="/register" v-if="!isLoggedIn">Sign-up</router-link>
        <router-link to="/login" v-if="!isLoggedIn">Log-in</router-link>
        <button class="sign-out" v-else v-on:click="logout">Sign out</button>
      </div>
    </nav>
  </div>
</template>

<script>
import firebase from 'firebase/app';
import 'firebase/auth';

export default {
  data() {
    return {
      isLoggedIn: false,
    };
  },
  beforeMount() {
    this.checkLoggedIn();
  },
  beforeUpdate() {
    this.checkLoggedIn();
  },
  methods: {
    checkLoggedIn() {
      firebase.auth().onAuthStateChanged((user) => {
        if (user) this.isLoggedIn = true;
        else this.isLoggedIn = false;
      });
    },
    logout() {
      firebase.auth().signOut();
      this.$router.push('/');
    },
  },
};
</script>

<style>
.nav-borders {
  border: 1px solid black;
}
.wrapper {
  margin: 0 auto;
  width: 1024px;
}

nav img {
  width: 8em;
}

nav {
  align-items: center;
  display: flex;
  justify-content: space-between;
  height: 12vh;
}

nav div a:first-child {
  color: #f87d7f;
}

nav div a {
  border-radius: 0.75rem;
  color: black;
  font-size: 1.25rem;
  padding: 0.75rem;
  margin-right: 0.75em;
  text-decoration: none;
}

nav div a:hover {
  background: #f87d7f;
  color: white;
  transition: 0.5s;
}

button.sign-out {
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
  font-size: 1.2rem;
  height: 2.5rem;
  width: 8rem;
}

button.sign-out:hover {
  background: #f87d7f;
  color: white;
  transition: 0.5s;
}
</style>
