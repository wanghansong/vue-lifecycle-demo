<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="toggleHandler">切换</button>
    <ChildA
      v-if="comp === 'ChildA'"
      @testClickA="testClickBHandlerA"
    ></ChildA>
    <ChildB v-else @testClickB="testClickBHandlerB"></ChildB>
  </div>
</template>

<script>
import ChildA from './child-a';
import ChildB from './child-b';

export default {
  name: 'parent-comp',
  props: {
    parentProp: {
      type: Object,
      default: ()=>({})
    }
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      comp: 'ChildA',
      toogle: true,
    }
  },

  provide: {
    parentVal: "parent val"
  },

  components: {
    ChildA,
    ChildB,
  },

  methods: {
    toggleHandler() {
      this.toogle = !this.toogle;
      this.comp = this.toogle ? 'ChildA' : 'ChildB';
    },
    testClickBHandlerA(val) {
      console.log(val);
      this.$emit('testClickParent', val);
    },
    testClickBHandlerB() {

    },
    toogleHandler() {
        console.log('hello');
    },
  },

  watch: {
    comp: {
      handler() {
        console.log('watch parent');
      },
      immediate: true
    },
  },

  beforeCreate () {
    console.log('parent beforeCreate');

  },

  created () {
    console.log('parent created');
  },

  beforeMount () {
    console.log('parent beforeMount');
  },

  mounted () {
    console.log('parent mounted');
    console.log('parent vm:', this, 'parent vm.$options:', this.$options);

  },

  beforeUpdate () {
    console.log('parent beforeUpdate');
  },

  updated () {
    console.log('parent updated');
  },

  beforeDestroy () {
    console.log('parent beforeDestroy');
  },

  destroyed () {
    console.log('parent destroyed');
  },

  activated() {
    console.log('parent activated');
  },

  deactivated() {
    console.log('parent deactivated');
  },

  errorCaptured() {
    console.log('parent errorCaptured');
  },

  serverPrefetch() {
    console.log('parent serverPrefetch');
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
