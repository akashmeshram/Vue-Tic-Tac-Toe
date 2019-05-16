<template>
  <button class="square" @click="$emit('onClick')">
        {{Value}}
  </button>
</template>

<script>

export default {
  name: 'Square',
  props: ['Value']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
