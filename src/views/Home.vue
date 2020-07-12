<template>
  <div class="home">
    <HelloWorld @onSubmit="submitContent"/>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  methods: {
    submitContent(content) {
      this.$router.push({name: "About", params: {content: content}})
    }
  }
}
</script>
