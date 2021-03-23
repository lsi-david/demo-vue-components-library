<script>
import Vue from 'vue';
// Uncomment import and local "components" registration if library is not registered globally.
import {SocialButton, FileInput} from '@/entry.esm';

export default Vue.extend({
  name: 'ServeDev',
  data() {
    return {
      file: null,
    };
  },
  components: {
    SocialButton,
    FileInput,
  },
  methods: {
    hello() {
      console.log('Hola mundo');
    },

    onChangeFile(e) {
      this.file = e.target.files[0];
      console.log(this.file.name);
    },

    onFileDrop(e) {
      e.stopPropagation();
      e.preventDefault();
      this.file = e.dataTransfer.files[0];
      console.log(this.file);
      document.getElementById('DropContainer').classList.remove('bg-green');
    },
  },
});
</script>

<template>
  <div id="app">
    <SocialButton
      :icon="'fab fa-facebook-f'"
      :background="'3B5998'"
      :onClick="hello"
    />
    <FileInput
      :id="'DropContainer'"
      :width="'150px'"
      :height="'100px'"
      :onChange="onChangeFile"
      :onDrop="onFileDrop"
    />
  </div>
</template>
