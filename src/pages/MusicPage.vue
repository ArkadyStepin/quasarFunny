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
        <h1>DropZone</h1>
        <DropZone @drop.prevent="drop" @change="selectedFile" />
        <span class="file-info">File: {{ dropzoneFile.name }}</span>
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
  },

  setup() {
    let reg = /audio/;
    let dropzoneFile = ref("");
    const drop = (e) => {
      dropzoneFile.value = e.dataTransfer.files[0];
      if (reg.test(dropzoneFile.value.type) === true) {
        console.log("zaebis");
      } else console.log("sosi");
    };

    const selectedFile = () => {
      dropzoneFile.value = document.querySelector(".dropzoneFile").files[0];
    };
    return { dropzoneFile, drop, selectedFile };
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
