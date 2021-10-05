<template>
  <section>
    <header>
      <h1>My Friends</h1>
    </header>
    <ul>
      <friend-contact
        name="Endi"
        id="1"
        email="tbd@kuka.com"
        phone="324232479243"
      ></friend-contact>
      <friend-contact
        name="Evan"
        id="2"
        email="tbd@kuka.com"
        phone="111112222233334444"
      ></friend-contact>
    </ul>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator"
import FriendContact from "./components/FriendContact.vue"

@Component({
  components: {
    FriendContact,
  },
})
export default class App extends Vue {
  friends = [
    {
      id: "manuel",
      name: "Manuel Lorenz",
      phone: "0123 45678 90",
      email: "manuel@localhost.com",
    },
    {
      id: "julie",
      name: "Julie Jones",
      phone: "0987 654421 21",
      email: "julie@localhost.com",
    },
  ]
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
* {
  box-sizing: border-box;
}
html {
  font-family: "Jost", sans-serif;
}
body {
  margin: 0;
}
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
</style>
