<template>
  <div :style="{ backgroundColor: color }"></div>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      required: true
    }
  },


}
</script>

<style scoped>
 div {
   height: 2rem;
   width: 2rem;
   border: 1px solid #333;
   border-radius: 50%;
   margin: 1rem 0;
 }
</style>