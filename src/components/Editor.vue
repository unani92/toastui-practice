<template>
  <div>
    <div id="editor"/>
    <button v-on:click="onChange">Submit</button>
  </div>
</template>
<script>
import 'codemirror/lib/codemirror.css'; // codemirror 스타일
import '@toast-ui/editor/dist/toastui-editor.css'; // Editor's Style
import Editor from '@toast-ui/editor';
import 'highlight.js/styles/github.css'; // code block highlight 스타일
import codeSyntaxHightlight from '@toast-ui/editor-plugin-code-syntax-highlight';
import hljs from 'highlight.js';

export default {
  data() {
    return {
      editorText: 'This is initialValue.',
      editorOptions: {
        hideModeSwitch: true
      }
    };
  },
  methods: {
    onChange() {
      const codeMirror = document.querySelector(".CodeMirror-code")
      const content = codeMirror.innerText
      this.$emit("onSubmit",content)
    }
  },
  mounted() {
    const editor = new Editor({
      el: document.querySelector("#editor"),
      initialEditType: "markdown",
      previewStyle: "vertical",
      height: "500px",
      plugins: [[codeSyntaxHightlight, { hljs }]]
    })
    editor
  }
};
</script>