<template>
  <div class="searchWrapper">
    <h1>Movies database</h1>
    <input
        id="search"
        name="search"
        type="text"
    />
  </div>
</template>

<script>
export default {
  name: "Search"
}
</script>

<style lang="scss" scoped>

.searchWrapper {
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  justify-content: center;
  font-size: 34px;
}


</style>
