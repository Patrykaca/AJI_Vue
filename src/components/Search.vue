<template>
    <div class="searchWrapper">

      <h1>Baza Filmów</h1>
      <div>
        <input type="text" id="inputSearch" placeholder="Type Your search here..."/>
      </div>

      <div>
        <input type="button" id="dateBtn" value="Search"/>
      </div>

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
