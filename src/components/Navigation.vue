<template>
  <div class="nav-borders mobile-container">
    <nav class="wrapper topnav">
      <router-link to="/"
        ><img
          src="https://i.pinimg.com/originals/8d/c5/31/8dc531fd1168a51c9e5bc9aca0d45051.jpg"
          alt="logo"
      /></router-link>

      <div id="myLinks">
        <router-link to="/favourites" alt="Favourites" v-if="isLoggedIn">&#10084;</router-link>
        <router-link to="/">Home</router-link>
        <router-link to="/add">Add recipe</router-link>
        <router-link to="/register" v-if="!isLoggedIn">Sign-up</router-link>
        <router-link to="/login" v-if="!isLoggedIn">Log-in</router-link>
        <button class="sign-out" v-on:click="logout" v-else>
          Sign out
        </button>
      </div>
      <div class="flexit">
        <a href="javascript:void(0);" class="icon" v-on:click="burger">
          &#9776;
        </a>
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
      localStorage.removeItem('token');

      this.$router.push('/');
    },
    burger() {
      const x = document.getElementById('myLinks');
      if (x.style.display === 'block') {
        x.style.display = 'none';
      } else {
        x.style.display = 'block';
      }
    },
  },
};
</script>

<style>
.flexit {
  display: flex;
  justify-content: space-between;
}
/* .mobile-container {
  max-width: 480px;
  margin: auto;
  background-color: rgb(189, 29, 29);
  height: 20vh;
  color: white;
  border-radius: 10px;
} */

.topnav {
  display: flex;
  margin: 0 auto;
  overflow: hidden;
  background-color: white;
  position: relative;
}

/* .topnav #myLinks {
  display: none;
} */

.topnav a {
  color: black;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
  display: block;
}

.topnav a.icon {
  display: block;
  background: white;
  display: block;
  position: absolute;
  right: 0;
  top: 0;
}

.active {
  background-color: #04aa6d;
  color: white;
}

/* .nav-borders {
  border: 1px solid black;
}
.wrapper {
  margin: 0 auto;
  width: 1024px;
}
*/
nav img {
  width: 10em;
}
/*
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
} */

button.sign-out:hover {
  background: #f87d7f;
  color: white;
  transition: 0.5s;
}
@media screen and (min-width: 1024px) {
  #myLinks {
    display: flex;
  }
  .topnav a.icon {
    display: none;
  }
  .wrapper {
    margin: 0 auto;
    width: 768px;
  }
  nav {
    display: flex;
    height: 12vh;
  }
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
}
</style>
