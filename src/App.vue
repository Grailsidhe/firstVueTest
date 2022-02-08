<template>
  <div id="app">
    <h1>Random User Generator</h1>
    <User
      :firstName="firstName"
      :lastName="lastName"
      :email="email"
      :photo="photo"
      :country="country"
      :city="city"
      :phone="phone"
      @get-user="getUser()"
    />
  </div>
</template>

<script>
import User from "./components/User";

export default {
  name: "App",
  components: {
    User,
  },
  data() {
    return {
      firstName: "Sarah",
      lastName: "Clark",
      email: "sarahclark@test.it",
      photo: "https://randomuser.me/api/portraits/women/1.jpg",
      country: "Michigan",
      city: "Michigan",
      phone: "52858297",
    };
  },
  methods: {
    async getUser() {
      const res = await fetch("https://randomuser.me/api");
      const { results } = await res.json();
      const user = results[0];
      this.firstName = user.name.first;
      this.lastName = user.name.last;
      this.email = user.email;
      this.photo = user.picture.large;
      this.country = user.location.country;
      this.city = user.location.city;
      this.phone = user.phone;
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
button {
  border: 0;
  margin: 20px;
  padding: 10px;
  background: rgb(3, 3, 12);
  color: white;
  text-transform: uppercase;
  border-radius: 5px;
  font-weight: 700;
  box-shadow: 2px 2px 2px 1px grey;
}
button:hover {
  color: rgb(243, 255, 191);
}
button:active {
  box-shadow: 1px var(--accent);
}
</style>
