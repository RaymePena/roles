<template>
  <div id="app">
    <Header />
    <div class="role-options">
      <h1>Select a role</h1>
      <select v-model="options.role" @change="showContent">
        <option v-for="role of roles" v-bind:key="role.name">
          {{ role.name }}
        </option>
      </select>
    </div>

    <div class="container" v-show="showContentI">
      <div class="foto">
        <img width="500px" height="700px" :src="image" />
      </div>
      <div class="title">
        <div class="content">
          <h2 @mouseover="hover = true" @mouseleave="hover = false">
            {{ options.role }}
          </h2>
          <div v-show="hover" class="hints">
            <p>Company: {{ options.company }}</p>
            <p>Language: {{ options.language }}</p>
          </div>
        </div>
      </div>
    </div>
    <!-- <img v-for="image in images" v-bind:src="customer" v-bind:key="image" /> -->
  </div>
</template>

<script>
import Header from "./components/Header";
export default {
  name: "App",
  components: {
    Header,
  },

  data() {
    return {
      hover: false,
      roles: [
        { name: "Customer", company: "Wanba", language: "English" },
        { name: "Tech Lead", company: "Adobe", language: "Spanish" },
        { name: "Mentor", company: "UVU", language: "English" },
        { name: "Narrator", company: "History Channel", language: "English" },
        { name: "Teacher", company: "Utah State", language: "English" },
      ],
      options: {
        role: "",
        company: "",
        language: "",
      },
      image: "",
      isContent: false,
      showContentI: false,
    };
  },
  created() {},
  methods: {
    showContent: function () {
      this.showContentI = true;
      this.roles.forEach((role) => {
        if (role.name === this.options.role) {
          this.options.company = role.company;
          this.options.language = role.language;
        }
      });

      if (this.options.role === "Tech Lead") {
        this.image = require(`./assets/techLead.png`);
      } else {
        this.image = require(`./assets/${this.options.role.toLowerCase()}.png`);
      }
    },
  },
};
</script>

<style scope>
body {
  margin: 0;
  padding: 0;
  font-family: "Courier New", Courier, monospace;
  box-sizing: border-box;
}
nav {
  width: auto;
  background: #669daf;
  height: 100px;
  text-align: center;
  padding: 10px;
  color: white;
}
nav h1 {
  margin: 20px auto;
  font-size: 2em;
  color: white;
  border: 3px dashed black;
  width: 10%;
  padding: 10px;
  border-radius: 25px;
}
.role-options {
  width: 40%;
  margin: 10px auto;
  border: 1px solid black;
  text-align: center;
  border-radius: 10px;
  padding: 10px;
  box-shadow: 2px 2px 4px #000000;
}
.role-options h1 {
  margin-bottom: 2px;
}
select {
  width: 70%;
  height: 50px;
  border-radius: 10px;
  font-size: 1.5em;
  margin-bottom: 30px;
}

.container {
  width: 1200px;
  text-align: center;
  display: grid;
  grid-template-columns: repeat(12, auto);
  gap: 10px;
  margin: 30px auto;
  background: #f4f4f4;
  padding: 30px;
  border-radius: 20px;
}

.foto {
  grid-row-start: 1;
  grid-row-end: 3;
  grid-column-start: 1;
  grid-column-end: 3;
  padding: 0px;
}
.title {
  grid-row-start: 1;
  grid-row-end: 3;
  grid-column-start: 3;
  grid-column-end: 12;
}
.content {
  width: 100%;
  padding: 10px;
  display: relative;
}
.hints {
  display: absolute;
  margin: 0 auto;
  width: 75%;
  left: 20px;
  background: grey;
  padding: 15px;
  border-radius: 25px;
  color: white;
  font-size: 1.5em;
}
.content h2 {
  width: 50%;
  margin: 30px auto;
  text-align: center;
  padding: 20px;
  border-radius: 15px;
  font-size: 2em;
}
.content h2:hover {
  background: #669daf;
  color: white;
}
.foto img {
  padding: 10px;
  box-shadow: 2px 2px 4px #000000;
}
</style>
