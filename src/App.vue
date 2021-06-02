<template>
  <nav class="wrapper">
    <router-link to="/"
      ><img
        src="https://i.pinimg.com/originals/8d/c5/31/8dc531fd1168a51c9e5bc9aca0d45051.jpg"
        alt="logo"
    /></router-link>

    <div>
      <router-link to="/favourites" alt="Favourites">&#10084;</router-link>
      <router-link to="/">Home</router-link>
      <router-link to="/add">Add recipe</router-link>
      <router-link to="/register">Sign-up</router-link>
      <router-link to="/login">Log-in</router-link>
    </div>
  </nav>
</template>

<script>
// import firebase from 'firebase/app';
// import 'firebase/auth';

export default {};
</script>

<style scoped>
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
</style>
