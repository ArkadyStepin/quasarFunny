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
    </div>
  </q-page>
</template>

<script>
import LeftAside from "../components/LeftAside.vue";
export default {
  components: { LeftAside },

  methods: {
    addFile() {
      const musicFiles = this.$refs.musicFile.files;
      const audioControll = this.$refs.audioControll;
      audioControll.src = URL.createObjectURL(musicFiles[0]);
      audioControll.load();
      audioControll.play();

      console.log(audioControll);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
