<template>
  <div class="row">
    
    <Blog v-for="b in blogs" :key="b.id" :blog="b"/>
    <!-- <div v-for="b in blogs" :key="b.id" :blogs="b" class="col-md-3 elevation-2 rounded bg-light">
      <h3> {{b.title}} </h3>
      <img class="img-fluid" :src="b.imgUrl" alt="">
      <p> {{b.body}} </p>
    </div> -->
    
  </div>
</template>

<script>
import { computed, onMounted } from "@vue/runtime-core"
import Pop from "../utils/Pop"
import { logger } from "../utils/Logger"
import { blogsService } from "../services/BlogsService"
import { AppState } from "../AppState"
import Blog from "../components/Blog.vue"
export default {
  components: { Blog },
  name: 'Home',
  setup(){
    onMounted(async () =>{
      try {
        await blogsService.getBlogs()
      } catch (error) {
        logger.error(error)
        Pop.toast(error.message, 'error')
      }
    });
  return {
    blogs: computed(() => AppState.blogs)
  }
  }
}
</script>

<style scoped lang="scss">
.home{
  display: grid;
  height: 80vh;
  place-content: center;
  text-align: center;
  user-select: none;
  .home-card{
    width: 50vw;
    > img{
      height: 200px;
      max-width: 200px;
      width: 100%;
      object-fit: contain;
      object-position: center;
    }
  }
}
</style>
