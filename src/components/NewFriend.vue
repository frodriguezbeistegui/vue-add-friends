<template>
<form @submit.prevent="addFriend">
  <div>
    <label>Name:</label>
    <input type="text" v-model="name" />
  </div>
  <div>
    <label>Phone Number:</label>
    <input type="tel" v-model="phone" />
  </div>
  <div>
    <label>E-mail:</label>
    <input type="email" v-model="email" />
  </div>
  <div>
    <label>Add to favourites</label>
    <input type="checkbox" @click="setFavourite" />
  </div>
  <button @click="addFriend">Add Friend!</button>
  </form>
</template>

<script>
export default {
    emits: ['add-new-friend'],
  data() {
    return {
      name: "",
      phone: "",
      email: "",
      isFavourite: false,
    };
  },
  methods: {
    setFavourite() {
      this.isFavourite = !this.isFavourite;
    },
    addFriend() {
      this.id = this.name;
      this.$emit(
        "add-new-friend",
        this.name,
        this.phone,
        this.email,
        this.isFavourite
      );
      this.id = "";
      this.name = "";
      this.phone = "";
      this.email = "";
      this.isFavourite = false;
    },
  },
};
</script>
