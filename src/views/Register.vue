<template>
  <section class="sign">
    <div class="down">
      <form v-on:submit.prevent="register">
        <h1>Sign-up</h1>
        <label class="label">Email</label>
        <div class="control">
          <input type="email" v-model="email" placeholder="Enter your email" />
        </div>

        <label class="label">Password</label>
        <div class="control">
          <input type="password" v-model="password" placeholder="*******" />
        </div>

        <div class="control buttons-right">
          <button type="submit">Sign-up</button>
        </div>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Register',
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    register() {
      fetch('http://localhost:3000/auth/register', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          email: this.email,
          password: this.password,
        }),
      })
        .then((res) => res.json())
        .then((data) => {
          console.log(data);
          localStorage.setItem('token', data.token);
          this.$router.push('/login');
        })
        .catch((e) => alert(e.message));
    },
  },
};
</script>

<style scoped>
section.sign {
  padding-top: 10rem;
  background: #f1f2f2;
}
form {
  background: url('https://p0.pikist.com/photos/744/884/knife-food-wood-table-wooden-background-meal-cooking-healthy.jpg');
  background-size: cover;
  width: 650px;
  margin: 0 auto;
  padding: 2rem;
  border-radius: 0.5rem;
}

div.control input {
  width: 100%;
  padding: 1em;
  margin: 1em 0;
  box-sizing: border-box;
  border-radius: 0.25em;
}

div.buttons-right {
  text-align: right;
  margin-top: 1em;
}

button {
  border: none;
  border-radius: 0.25rem;
  width: 7rem;
  height: 4rem;
  cursor: pointer;
}

button:hover {
  background: #f87d7f;
  color: white;
  transition: 0.5s;
}
</style>
