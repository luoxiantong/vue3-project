<template>
  <img
    alt="Vue logo"
    src="../assets/logo.png"
  />
  <h1>{{ msg }}</h1>
  <!-- <button @click="inCrement"> count is: </button> -->
  <el-button
    icon="el-icon-success"
    type="primary"
    @click="inCrement"
  >增加</el-button>
  count is: {{ count }}
  <el-button
    icon="el-icon-success"
    type="primary"
    @click="decreaseCrement"
  >减少</el-button>
</template>

<script>
import { defineComponent, computed } from 'vue'
import { useStore } from 'vuex'
import { key } from '../store'

export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: {
      type: String,
      default: 'Hello Vue 3 + TypeScript + Vite'
    }
  },
  setup() {
    const store = useStore(key)
    console.log(store,useStore(key));
    const count = computed(() => store.state.count)

    return {
      count,
      inCrement: () => store.commit('increment'),
      decreaseCrement: () => store.commit('decreaseCrement'),
    }
  }
})
</script>
