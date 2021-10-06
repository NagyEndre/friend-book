<template>
  <li>
    <h2>{{ friend.name }} {{ friend.isFavorite ? "(Favorite)" : "" }}</h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <button @click="deleteFriend" class="danger">Delete</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ friend.phone }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ friend.email }}
      </li>
    </ul>
  </li>
</template>

<script lang="ts">
import { Component, Vue, Prop, Emit } from "vue-property-decorator"
import { Friend } from "../Friend"

@Component
export default class FriendContact extends Vue {
  detailsAreVisible = true

  @Prop({ type: Object, required: true }) friend!: Friend

  @Emit()
  toggleFavorite() {
    return this.friend.id
  }

  toggleDetails() {
    this.detailsAreVisible = !this.detailsAreVisible
  }

  @Emit()
  deleteFriend() {
    return this.friend.id
  }
}
</script>

<style scoped>
li li {
  margin: 0.5rem 0;
}
</style>
