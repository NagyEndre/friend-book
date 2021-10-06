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
import { Vue, Component, Emit } from "vue-property-decorator"
import { Friend } from "../Friend"

@Component
export default class NewFriend extends Vue {
  name = ""
  phoneNumber = ""
  email = ""
  isFavorite = false
  id = -1

  @Emit()
  submitNewFriend() {
    const newFriend: Friend = {
      name: this.name,
      id: this.id,
      email: this.email,
      phone: this.phoneNumber,
      isFavorite: this.isFavorite,
    }
    console.log(newFriend)
    return newFriend
  }
}
</script>
