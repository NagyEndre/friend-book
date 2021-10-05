<template>
  <section>
    <header>
      <h1>My Friends</h1>
    </header>
    <ul>
      <friend-contact
        v-for="friend in friends"
        :key="friend.id"
        :friend="friend"
        @toggle-favorite="toggleFavorite"
      ></friend-contact>
    </ul>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator"
import FriendContact from "./components/FriendContact.vue"
import { Friend } from "./Friend"

@Component({
  components: {
    FriendContact,
  },
})
export default class App extends Vue {
  friends: Friend[] = [
    {
      id: 1,
      name: "Manuel Lorenz",
      phone: "0123 45678 90",
      email: "manuel@localhost.com",
      isFavorite: true,
    },
    {
      id: 2,
      name: "Julie Jones",
      phone: "0987 654421 21",
      email: "julie@localhost.com",
      isFavorite: false,
    },
  ]
  toggleFavorite(friendId: number) {
    const identifiedFriend: Friend = this.friends.find(
      (friend) => friend.id === friendId
    )!
    identifiedFriend.isFavorite = !identifiedFriend.isFavorite
  }
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
