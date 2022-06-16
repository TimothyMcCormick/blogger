<template>
  <div class="container-fluid">
    <div class="row justify-content-center">
      <div class="col-md-10 d-flex flex-column justify-content-center">
        <h3 class="text-center"> {{activeBlog.title}} </h3>
        <img class="img-fluid " :src="activeBlog.imgUrl" alt="">
        <p class="text-center"> {{activeBlog.body}} </p>
      </div>
    </div>
  </div>
</template>


<script>
import { computed } from "@vue/reactivity"
import { AppState } from "../AppState"
import { onMounted } from "@vue/runtime-core"
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