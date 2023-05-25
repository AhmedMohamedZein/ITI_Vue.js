<template>
  <div>
    <h4>Admin Details</h4>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Age</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="admin in admins" :key="admin.name">
          <td>{{ admin.name }}</td>
          <td>{{ admin.age }}</td>
          <td>
            <button @click="deleteAdmin(admin)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
  
  <script>
export default {
  name: "AdminDetailsComponent",
  props: {
    admins: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    deleteAdmin(admin) {
      // Emit an event to the parent component to delete the admin
      this.$emit("delete-admin", admin);
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
  