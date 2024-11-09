<template>
  <div class = "container">
    <header>
      <h1> New Member Info page </h1>
    </header>
  </div>
  <div class = "Info">

    <p>Tryout dates: </p>
    <p> Sign up form </p>
    <p> Sports waiver </p>
  </div>

</template>

/*router.push({ path: '/new-page', query: { userId: 123 } });*/
<script setup lang="ts">

</script>
<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;

}
.Info{
  flex:1;
  margin-left: 100px;
}
</style>