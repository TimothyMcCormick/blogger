<template>
  <router-link :to="{ name: 'Blog', params: { id: blog.id }}">
  <div class="col-md-3 elevation-2 rounded bg-light selectable" @click="setActive">
      <h3> {{ blog.title }} </h3>
      <img class="img-fluid" :src="blog.imgUrl" alt="">
      <p> {{ blog.body }} </p>
    </div>
  </router-link>

</template>


<script>
import { blogsService } from "../services/BlogsService"
import { logger } from "../utils/Logger"
export default {
  props: { blog: { type: Object, required: true }  },
  setup(props){
    return {
      setActive(){
        blogsService.setActive(props.blog)
        logger.log('getting blog')
      }
    }
  }
}
</script>


<style lang="scss" scoped>

</style>