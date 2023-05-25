<template>
  <div>
    <h4>User Details</h4>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Age</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.name">
          <td>{{ user.name }}</td>
          <td>{{ user.age }}</td>
          <td>
            <button @click="deleteUser(user)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
  
  <script>
export default {
  name: "UserDetailsComponent",
  props: {
    users: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    deleteUser(user) {
      // Emit an event to the parent component to delete the user
      this.$emit("delete-user", user);
    },
  },
};
</script>
  
  <style scoped>
table {
  border-collapse: collapse;
  width: 15%;
}

th,
td {
  border: 1px solid #ddd;
  padding: 8px;
}

th {
  background-color: #f2f2f2;
}
</style>
  