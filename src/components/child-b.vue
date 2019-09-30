<template>
<div>
  <div>child B</div>
  <button @click="testClick">testB emit</button>
</div>
</template>

<script>
export default {
  name: 'child-b',

  methods: {
    testClick() {
      this.$emit('testClickB', 123)
    }
  },

  beforeCreate () {
    console.log('child b beforeCreate');

  },

  created () {
    console.log('child b created');
  },

  beforeMount () {
    console.log('child b beforeMount');
  },

  mounted () {
    console.log('child b  mounted');
  },

  beforeUpdate () {
    console.log('child b beforeUpdate');
  },

  updated () {
    console.log('child b updated');
  },

  beforeDestroy () {
    console.log('child b beforeDestroy');
  },

  destroyed () {
    console.log('child b destroyed');
  }
}
</script>

<style>

</style>