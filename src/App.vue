<template>
  <section id="app">
    <header>
      <h1>My Friends</h1>
    </header>
    <new-friend class="card" @submit-new-friend="onNewFriendSubmitted" />
    <ul>
      <friend-contact
        v-for="friend in friends"
        :key="friend.id"
        :friend="friend"
        @toggle-favorite="toggleFavorite"
        class="card"
      ></friend-contact>
    </ul>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator"
import FriendContact from "./components/FriendContact.vue"
import { Friend } from "./Friend"
import NewFriend from "./components/NewFriend.vue"

@Component({
  components: {
    FriendContact,
    NewFriend,
  },
})
export default class App extends Vue {
  friends: Friend[] = []
  toggleFavorite(friendId: string) {
    const identifiedFriend: Friend = this.friends.find(
      (friend) => friend.id === friendId
    )!
    identifiedFriend.isFavorite = !identifiedFriend.isFavorite
  }
  onNewFriendSubmitted(newFriend: Friend) {
    console.log("onNewFriendSubmitted")
    this.friends.unshift(newFriend)
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
  background-color: royalblue;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
.card {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: mediumblue;
  margin: 0 0 1rem 0;
}
button {
  font: inherit;
  cursor: pointer;
  border: 1px solid mediumblue;
  background-color: mediumblue;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  margin: 0 0.25rem;
}
button:hover,
button:active {
  background-color: royalblue;
  border-color: royalblue;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>
