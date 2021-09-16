<template>
  <div id="inputshow">
      <p class="inputTemp">{{ inputTemp }}</p>
      <p class="inputVal">{{ inputVal }}</p>
  </div>
</template>

<script>
export default {
    props: {
        inputTemp: String,
        inputVal: String
    }
}
</script>

<style>

</style>