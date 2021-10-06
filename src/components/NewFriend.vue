<template>
  <form @submit.prevent="submitNewFriend">
    <h2>Add new friend</h2>
    <div>
      <label for="">Name</label>
      <input type="text" v-model="name" />
    </div>
    <div>
      <label for="">Phone</label>
      <input type="tel" v-model="phoneNumber" />
    </div>
    <div>
      <label for="">Email</label>
      <input type="email" v-model="email" />
    </div>
    <div>
      <label for="">Favorite</label>
      <input type="checkbox" v-model="isFavorite" />
    </div>
    <button type="submit">Add</button>
  </form>
</template>
<script lang="ts">
import { Friend } from "@/Friend"
import { Vue, Component, Emit } from "vue-property-decorator"

@Component
export default class NewFriend extends Vue {
  name = ""
  phoneNumber = ""
  email = ""
  isFavorite = false

  @Emit()
  submitNewFriend() {
    const newFriend: Friend = {
      name: this.name,
      id: new Date().toISOString(),
      email: this.email,
      phone: this.phoneNumber,
      isFavorite: this.isFavorite,
    }
    this.resetInputs()
    console.log(newFriend)
    return newFriend
  }
  private resetInputs() {
    this.name = ""
    this.phoneNumber = ""
    this.email = ""
    this.isFavorite = false
  }
}
</script>

<style scoped>
input {
  font: inherit;
  padding: 0.15rem;
}
label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
form div {
  margin: 1rem 0;
}
</style>
>
