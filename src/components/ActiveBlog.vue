<template>
  
    
  active blog
  
</template>


<script>
import { computed } from "@vue/reactivity"
import { AppState } from "../AppState"
export default {
  setup(){
    return {
      activeBlog: computed(() => AppState.activeBlog)
    }
  }
}
</script>


<style lang="scss" scoped>

</style>