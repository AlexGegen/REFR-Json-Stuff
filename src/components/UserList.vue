<template>
  <div>
    <div v-if="error">
      <h2>{{ error }}</h2>
    </div>
    <div v-else>
      <div v-if="loading">
        <h2>Loading data...</h2>
      </div>
    </div>
    <h1>Users</h1>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Username</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="item in data">
          <td>{{ item.name }}</td>
          <td>{{ item.username }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { useFetch } from '../composable/UseFetch.js';

export default {
  setup() {
    const { data, error, loading } = useFetch(
      'https://jsonplaceholder.typicode.com/users',
      {}
    );
    return {
      data,
      error,
      loading,
    };
  },
};
</script>

<style></style>
