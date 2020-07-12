<template>
  <div class="about">
    <div id="viewer"/>
  </div>
</template>
<script>
  import Viewer from '@toast-ui/editor/dist/toastui-editor-viewer';
  import '@toast-ui/editor/dist/toastui-editor-viewer.css'; // Editor's Style
  import 'highlight.js/styles/github.css'; // code block highlight 스타일
  import codeSyntaxHightlight from '@toast-ui/editor-plugin-code-syntax-highlight';
  import hljs from 'highlight.js';
  export default {
    name: "About",
    data() {
      return {
        content: null
      }
    },
    props: {
      params: Object
    },
    methods: {
      getContent() {
        const { content } = this.$router.currentRoute.params
        this.content = content
      }
    },
    mounted() {
      this.getContent()
      const viewer = new Viewer({
        el: document.querySelector("#viewer"),
        initialValue: this.content,
        plugins: [[codeSyntaxHightlight, { hljs }]]
      })
      console.log(viewer)
    }
  }
</script>
