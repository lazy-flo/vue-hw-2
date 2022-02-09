<template>
  <img :src="$attrs.value">
</template>

<script>
export default {
  name: 'FormAvatar'
}
</script>

<style scoped>
 img {
  height: 170px;
   width: 170px;
   /*border-radius: 50%;*/
 }

</style>
