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
        <DropZone @drop.prevent="drop" ref="dropMusicFile" />
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
      const canvas = this.$refs.canvasDiv;
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      const ctx = canvas.getContext("2d");
      let audioSource;
      let analyser;
      audioControll.src = URL.createObjectURL(musicFiles[0]);
      audioControll.load();
      // audioControll.play();
      const audioContext = new AudioContext();

      audioSource = audioContext.createMediaElementSource(audioControll);
      console.log(audioControll);
      analyser = audioContext.createAnalyser();
      audioSource.connect(analyser);
      analyser.connect(audioContext.destination);
      analyser.fftSize = 2048;
      const bufferLength = analyser.frequencyBinCount;
      const dataArray = new Uint8Array(bufferLength);

      const barWidth = canvas.width / 2.5 / bufferLength;
      let barHeight;
      let x;

      function drawVisualiser(bufferLength, x, barWidth, barHeight, dataArray) {
        for (let i = 0; i < bufferLength; i++) {
          barHeight = dataArray[i] * 2.5;
          ctx.save(); // точка сохранения
          ctx.translate(canvas.width / 2, canvas.height / 2);
          ctx.rotate((i * Math.PI * 2.2) / bufferLength);

          // // =======Один вид покраса===================

          const red = i + barHeight / 35;
          const green = barHeight / (i - 25);
          const blue = barHeight + 50;
          ctx.fillRect(0, 0, barWidth, 20);
          ctx.fillStyle = "rgb(" + red + ", " + green + ", " + blue + ")";

          // ===================Другой вид покраса(по ргб кругу)============

          // const hue = i * 3;
          // ctx.fillStyle = 'hsl(' + hue + ', 100%, 50%)';

          //=====================================

          ctx.fillRect(0, 0, barWidth, barHeight);
          x += barWidth;
          ctx.restore();
        }
      }

      function animate() {
        x = 0;
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        analyser.getByteFrequencyData(dataArray);
        drawVisualiser(bufferLength, x, barWidth, barHeight, dataArray);
        requestAnimationFrame(animate);
      }
      animate();
      // console.log(audioControll);
    },

    // работает ток с 1 файлом, будь человеком, мапни все
    drop(e) {
      let reg = /audio/;
      let dropzoneFile = ref("");
      const audioControll = this.$refs.audioControll;
      // const canvas = this.$refs.canvasDiv;

      dropzoneFile = e.dataTransfer.files[0];
      if (reg.test(dropzoneFile.type) === true) {
        audioControll.src = URL.createObjectURL(dropzoneFile);
        audioControll.load();
        console.log("zaebis");
      } else console.log("sosi");
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
