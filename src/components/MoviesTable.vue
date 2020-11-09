<template>
  <div class="tableWrapper">
    <table class="table">
      <thead>
      <tr>
        <th>Title</th>
        <th>Year</th>
        <th>Cast</th>
        <th>Genres</th>
      </tr>
      </thead>
      <tbody>
      <tr>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  name: "MoviesTable",
}
</script>

<style lang="scss" scoped>

.tableWrapper {
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  justify-content: center;
}

th {
  font-size: 40px;
  padding: 0 20px 0 20px;
  letter-spacing: 2px;
  font-weight: 400;
  color: #4a4a4a;
  text-shadow: 0 0 5px rgba(94,171,94, 0.4);
}

</style>
