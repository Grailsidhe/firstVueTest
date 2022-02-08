<template>
  <div class="contaniner">
    <div class="user-container">
      <img :src="photo" :alt="`${firstName} ${lastName}`" />
      <a :href="`mailto:${email}`" class="name"
        >{{ firstName }} {{ lastName }}</a
      >
      <p># {{ phone }}</p>
      {{ city }}, {{ country }}
    </div>
    <button @click="$emit('get-user')">Get new user</button>
  </div>
</template>

<script>
export default {
  name: "User",
  props: {
    firstName: { String, default: "Ana" },
    lastName: { String, default: "Clark" },
    photo: {
      String,
      default: "https://randomuser.me/api/portraits/women/1.jpg",
    },
    email: { String, default: "ana@clark.to" },
    city: { String, default: "Chicago" },
    country: { String, default: "United States" },
    phone: { String, default: "02 123 4567" },
  },
  emits: ["get-user"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: flex;
  flex-direction: column;
  padding: 10px;
}
.user-container {
  background-color: rgba(207, 224, 230, 0.562);
  display: flex;
  align-items: center;
  flex-direction: column;
  padding: 10px;
  border-radius: 10px;
  border: solid 1px grey;
  width: 180px;
  margin: auto;
  font-size: 0.8em;
}
p {
  margin: 5px 0;
}
img {
  border-radius: 50px;
  border: dotted 2px grey;
  height: 100px;
  width: 100px;
  margin: 5px 0 10px;
}
.name {
  font-weight: 600;
  font-size: 1.4em;
  text-decoration: none;
  color: rgb(19, 22, 32);
}
</style>
