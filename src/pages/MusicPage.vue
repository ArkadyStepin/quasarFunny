<template>
  <q-page class="row no-wrap justify-between">
    <left-aside />
    <div class="content">
      <div>
        Это музыкальная страничка, сюда ты можешь подгрузить свою музыку, а
        специальный алгоритм заколбасит это все в прикольную цетовую мазню
      </div>
      <div>
        Принци работы прост. В зависимости от частоты, и тд и тп, потом напишу
        ща чет подзабыл как че там работает
      </div>
      <div class="full-width">
        <input type="file" accept="audio/*" @change="addFile" ref="musicFile" />
        <audio controls ref="audioControll"></audio>
        <canvas ref="canvasDiv"></canvas>
      </div>
      <div class="home">
        <DropZone
          @drop.prevent="dropTest"
          @change="selectedFile"
          ref="dropMusicFile"
        />
      </div>
    </div>
  </q-page>
</template>

<script>
import { ref } from "vue";
import LeftAside from "../components/LeftAside.vue";
import DropZone from "../components/DropZone.vue";
export default {
  components: { LeftAside, DropZone },
  name: "MusicPage",

  methods: {
    addFile() {
      const musicFiles = this.$refs.musicFile.files;
      const audioControll = this.$refs.audioControll;
      audioControll.src = URL.createObjectURL(musicFiles[0]);
      audioControll.load();
      audioControll.play();

      // console.log(audioControll);
    },
    // работает ток с 1 файлом, будь человеком, мапни все
    dropTest(e) {
      let reg = /audio/;
      let dropzoneFile = ref("");
      dropzoneFile = e.dataTransfer.files[0];
      console.log(dropzoneFile);
      if (reg.test(dropzoneFile.type) === true) {
        // const dropMusicFiles = this.$refs.dropMusicFile.files;
        // console.log(dropMusicFiles);
        console.log("zaebis");
      } else console.log("sosi");
    },

    selectedFile() {
      dropzoneFile.value = document.querySelector(".dropzoneFile").files[0];
      console.log(dropzoneFile.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.home {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f1f1f1;
}

.file-info {
  margin-top: 32px;
}
</style>
