<template>
  <UserDetailsComponent :users="users" @delete-user="deleteUser" />
  <AdminDetailsComponent :admins="admins" @delete-admin="deleteAdmin" />
  <div>
    <form @submit.prevent="add">
      <div>
        <span>name: </span> <input type="text" v-model="formInput.name" />
      </div>
      <div><span>age: </span><input type="text" v-model="formInput.age" /></div>

      <label>
        <input type="radio" v-model="formInput.role" value="user" /> User
      </label>
      <label>
        <input type="radio" v-model="formInput.role" value="admin" /> Admin
      </label>
      <button type="submit">Add</button>
    </form>
  </div>
</template>
  
  <script>
import UserDetailsComponent from "../UserDetails/UserDetailsComponent.vue";
import AdminDetailsComponent from "../AdminDetails/AdminDetailsComponent.vue";

export default {
  name: "registerForm",
  components: {
    UserDetailsComponent,
    AdminDetailsComponent,
  },
  data() {
    return {
      users: [],
      admins: [],
      formInput: {
        name: "",
        age: "",
        role: "", // Updated to use radio input
      },
    };
  },
  methods: {
    add() {
      if (this.formInput.role === "user") {
        this.users.push({
          name: this.formInput.name,
          age: this.formInput.age,
        });
      } else if (this.formInput.role === "admin") {
        this.admins.push({
          name: this.formInput.name,
          age: this.formInput.age,
        });
      }
      this.formInput.name = "";
      this.formInput.age = "";
      this.formInput.role = "";
    },

    deleteUser(user) {
      const index = this.users.findIndex((u) => u === user);
      if (index !== -1) {
        this.users.splice(index, 1);
      }
    },
    deleteAdmin(admin) {
      const index = this.admins.findIndex((a) => a === admin);
      if (index !== -1) {
        this.admins.splice(index, 1);
      }
    },
  },
};
</script>
  

<style scoped>
form {
  height: 50vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

form input {
  background-color: #d6f294;
  max-width: 190px;
  height: 10px;
  padding: 10px;
  border: 2px solid white;
  border-radius: 5px;
  margin-bottom: 0.5em;
}

form input:focus {
  color: rgb(0, 0, 0);
  background-color: #d6f294;
  outline-color: rgb(0, 255, 255);
  box-shadow: -3px -3px 15px rgb(0, 255, 255);
  transition: 0.1s;
  transition-property: box-shadow;
}

div {
  display: flex;
  justify-content: center;
  align-content: center;
}
span {
  font: bold;
  font-size: large;
  margin-right: 1.5em;
}

    button {
        background-color: #dea53c;
        width: 20vh;
        height: 4vh;
        border-radius: 5px;
        
    }
</style>