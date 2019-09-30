<template>
  <div>
    <div>child a</div>
    <button @click="testClick">testA emit</button>
  </div>
</template>

<script>
export default {
  name: 'child-a',

  inject: ['parentVal'],

  props: {
    childAProp: {
      type: Object,
      default: ()=>({})
    }
  },

  data () {
    return {
      dataA: 'comp a data',
      watchHandler: 'watch is a object'
    }
  },

  methods: {
    testClick() {
      this.$emit('testClickA', 123)
    }
  },

  watch: {
    dataA() {
      console.log('child a watch');

    },
    watchHandler: {
        handler() {
            console.log('watchHandler');
        },
        deep: true,
    }
  },

  beforeCreate () {
    console.log('child a beforeCreate');

  },

  created () {
    console.log('child a created');
  },

  beforeMount () {
    console.log('child a beforeMount');
  },

  mounted () {
    console.log('child a mounted');
    console.log('childA vm:', this, 'childA vm.$options:', this.$options);
  },

  beforeUpdate () {
    console.log('child a beforeUpdate');
  },

  updated () {
    console.log('child a updated');
  },

  beforeDestroy () {
    console.log('child a beforeDestroy');
  },

  destroyed () {
    console.log('child a destroyed');
  },


}
</script>

<style>

</style>