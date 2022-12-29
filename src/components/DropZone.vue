<template>
  <div
    @dragenter.prevent="toggleActive"
    @dragleave.prevent="toggleActive"
    @dragover.prevent
    @drop.prevent="toggleActive"
    :class="{ 'active-dropzone': active }"
    class="dropzone"
  >
    <!-- <span>Drag or Drop File</span>
    <span>OR</span> -->
    <label for="dropzoneFile">Select File</label>
    <input
      type="file"
      ref="musicFile"
      @change="readFile"
      id="dropzoneFile"
      class="dropzoneFile"
      accept="audio/*"
    />
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "DropZone",


  // setup() {
  //   const active = ref(false);
  //   const toggleActive = () => {
  //     active.value = !active.value;
  //   };
  //   return { active, toggleActive };
  // },

  methods: {
    readFile() {
      const musicFiles = this.$refs.musicFile.files;
      console.log(musicFiles);
    },
  },
};
</script>

<style scoped lang="scss">
.dropzone {
  width: 400px;
  height: 200px;
  row-gap: 16px;
  border: 2px dashed #41b883;
  background-color: #fff;
  transition: 0.3s ease all;
  label {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    color: #41b883;
    transition: 0.3s ease all;
  }
  input {
    display: none;
  }
}
.dropzone:hover {
  background: #41b8835a;
}
.active-dropzone {
  color: #fff;
  border-color: #fff;
  background-color: #41b883;
  label {
    background-color: #fff;
    color: #41b883;
  }
}
</style>
