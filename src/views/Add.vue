<template>
  <div class="add">
    <form v-on:submit.prevent="add">
      <h1>Add your recipe</h1>
      <label class="label">Image</label>
      <div class="control">
        <input type="text" v-model="image" placeholder="Enter image url" />
      </div>

      <label class="label">Title</label>
      <div class="control">
        <input type="text" v-model="title" placeholder="Title" />
      </div>

      <label class="label">Description</label>
      <div class="control">
        <textarea
          class="textarea"
          v-model="description"
          placeholder="Your recipe description..."
        ></textarea>
      </div>

      <div class="control buttons-right">
        <button type="submit">Add</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      image: '',
      title: '',
      description: '',
    };
  },
  methods: {
    add() {
      fetch('http://localhost:3000/recipes', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          image: this.image,
          title: this.title,
          description: this.description,
        }),
      })
        .then((res) => res.json())
        .then((data) => {
          console.log(data);
          alert('Succesfully added recipe');
          this.$router.push('/');
        })
        .catch((e) => alert(e.message));
    },
  },
};
</script>

<style scoped>
.add {
  padding-top: 5em;
}

form {
  width: 650px;
  margin: 0 auto;
  padding: 3rem;
}

div.control input {
  width: 100%;
  padding: 1em;
  margin: 1em 0;
  box-sizing: border-box;
  border-radius: 0.25em;
}

h1 {
  text-align: center;
  padding-bottom: 2rem;
}

div.buttons-right {
  text-align: right;
  margin-top: 1em;
}

button {
  background: #f87d7f;
  border: none;
  border-radius: 0.25rem;
  width: 7rem;
  height: 4rem;
  cursor: pointer;
}

button:hover {
  background: black;
  color: white;
  transition: 0.5s;
}
.textarea {
  width: 100%;
  height: 10vh;
  box-sizing: border-box;
  border-radius: 0.25em;
  padding: 1em;
  max-width: 650px;
  max-height: 25vh;
  margin-top: 1em;
}
</style>
