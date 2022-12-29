<template>
  <div
    @dragenter.prevent="toggleActive"
    @dragleave.prevent="toggleActive"
    @dragover.prevent
    @drop.prevent="toggleActive"
    :class="{ 'active-dropzone': active }"
    class="dropzone"
  >
    <span></span>
    <label for="dropzoneFile" class="text-center"
      >Drag and drop file, <br />
      or tap here for select file</label
    >
    <input
      type="file"
      id="dropzoneFile"
      class="dropzoneFile"
      accept="audio/*"
    />
  </div>
</template>

<script>
export default {
  name: "DropZone",

  data() {
    return {
      active: false,
    };
  },
  methods: {
    toggleActive() {
      this.active = !this.active;
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
}
</style>
