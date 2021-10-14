<template>
  <div>
        <h1>Welcome to Random Blog</h1>
        <main>
          <PostBox/>
        </main>
    </div>
</template>

<script>
import PostBox from "../components/PostBox.vue"

export default {
  name: 'Home',
  components: {
    PostBox
  }
}
</script>
