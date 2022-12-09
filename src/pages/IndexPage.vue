<template>
  <q-page class="row no-wrap justify-between">
    <aside class="menu-column column no-wrap">
      <q-btn label="Стартовая страничка" flat style="color: #ff0080" />
      <q-btn label="ToDo лист" flat style="color: #ff0080" />
      <q-btn label="Музыкальная" flat style="color: #ff0080" @click="test" />
      <q-btn label="and more..." flat style="color: #ff0080" />
    </aside>
    <div class="content-column">
      <main class="text-h3 q-ma-sm">
        <q-card
          style="background: radial-gradient(circle, #8c47e0 0%, #ff0080 100%)"
        >
          <div class="row no-wrap flex-center q-mb-md">
            <q-icon name="keyboard_double_arrow_down" />
            <span class="text-h4 text-center">
              эта страничка создана по фану, что бы не терять скил в кодинге
            </span>
            <q-icon name="keyboard_double_arrow_down" />
          </div>
        </q-card>
        <div class="q-my-xl">скроль меня полностью!</div>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque ac
        est est. Phasellus eu metus a est semper fringilla. Vestibulum rutrum
        cursus luctus. Vestibulum eget dolor nec mi venenatis convallis. Sed sit
        amet dui sit amet ipsum lacinia lobortis. Mauris dictum purus ut tellus
        auctor, a blandit tortor lobortis. Pellentesque quam odio, porttitor non
        lacinia gravida, mattis a libero. Pellentesque rutrum augue id luctus
        sodales. Vestibulum sit amet risus ac turpis interdum vehicula.
        Suspendisse a libero nec ligula porta tempor. Nulla quis sapien porta,
        pharetra sapien sit amet, auctor risus. Donec sagittis libero ac mi
        finibus tristique. Cras vitae nunc venenatis, auctor nulla at, ultricies
        purus. Duis mi erat, dictum ac lobortis vitae, sodales eget nulla.
        Nullam in massa ut enim varius volutpat quis a tortor. Morbi eu ipsum
        dui. Curabitur mollis leo scelerisque est porttitor, eget lacinia purus
        maximus. Nullam ac tincidunt leo. Quisque maximus odio leo, quis
        convallis mauris imperdiet ac. Orci varius natoque penatibus et magnis
        dis parturient montes, nascetur ridiculus mus. Integer augue purus,
        congue eget erat vel, ornare tempus urna. Integer mattis pulvinar risus,
        sit amet mattis diam euismod non. Suspendisse potenti. Vestibulum
        pulvinar, risus ut imperdiet hendrerit, mi nibh varius lacus, eget
        fermentum ex nunc a lectus. Nam mollis massa ut risus rhoncus, eget
        suscipit ligula posuere. Proin mollis, urna sed imperdiet iaculis, massa
        est mollis urna, vel vehicula purus orci eget massa. Proin at placerat
        velit. Morbi mollis erat consectetur purus pharetra, ac auctor dui
        fermentum. Aenean et feugiat sem, sed interdum libero. Aenean bibendum
        ante a mauris iaculis, ac sollicitudin velit aliquet. Donec vel ultrices
        ex. Proin ac laoreet quam. Suspendisse auctor malesuada tellus, at
        congue odio luctus non. Praesent congue eleifend est, nec convallis mi
        dictum quis. Donec ultricies tempus lorem, vel hendrerit sapien iaculis
        non. Cras id augue id neque facilisis placerat a vitae sem. Phasellus
        iaculis dui nunc, ut consequat lacus mattis vitae. Nunc laoreet a tellus
        in dictum. Nulla ut venenatis velit. Nunc interdum finibus lectus, ac
        pulvinar dui cursus vitae. Aliquam sit amet lorem varius, pellentesque
        diam non, interdum nisl. Morbi efficitur libero non fermentum luctus.
        Nullam aliquet tortor sit amet arcu volutpat, ac accumsan dui tincidunt.
        Interdum et malesuada fames ac ante ipsum primis in faucibus. Mauris id
        erat vitae lacus mollis fringilla quis mattis augue. In laoreet bibendum
        enim, ac tempus elit ultricies quis. Vivamus sit amet lorem eu nisl
        facilisis consectetur. Sed nibh lectus, congue eu fringilla non,
        dignissim eget sem. Ut a est quam. Nulla sed condimentum risus. Praesent
        congue felis sed consectetur luctus. Pellentesque urna ex, egestas eu ex
        et, mollis luctus mauris. Aliquam quis feugiat odio, eu pulvinar leo.
        Generated 5 paragraphs, 438 words, 2875 bytes of Lorem Ipsum
      </main>
    </div>
    <aside class="funy-scroll-column text-center column no-wrap q-gutter-y-md">
      <div :class="{ getColor: isActiveColor0 }">Когда</div>
      <div :class="{ getColor: isActiveColor1 }">Ты</div>
      <div :class="{ getColor: isActiveColor2 }">Скролишь</div>
      <div :class="{ getColor: isActiveColor3 }">Подсвечиваются</div>
      <div :class="{ getColor: isActiveColor4 }">Разные</div>
      <div :class="{ getColor: isActiveColor5 }">Участки</div>
      <div :class="{ getColor: isActiveColor6 }">Этого</div>
      <div :class="{ getColor: isActiveColor7 }">Текста</div>
      <div :class="{ getColor: isActiveColor8 }">Зачем?</div>
      <div :class="{ getColor: isActiveColor9 }">Да прст)0)</div>
    </aside>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",

  mounted() {
    window.addEventListener("scroll", this.funyScroll);
  },

  beforeDestroy() {
    window.removeEventListener("scroll", this.funyScroll);
  },

  data() {
    return {
      isActiveColor0: true,
      isActiveColor1: false,
      isActiveColor2: false,
      isActiveColor3: false,
      isActiveColor4: false,
      isActiveColor5: false,
      isActiveColor6: false,
      isActiveColor7: false,
      isActiveColor8: false,
      isActiveColor9: false,
    };
  },

  methods: {
    test() {
      this.$router.push("/music");
    },

    funyScroll() {
      const allPageHeight = document.body.scrollHeight - window.innerHeight;
      const positinY = window.scrollY;
      const percentY = Math.round((positinY * 100) / allPageHeight);

      if (percentY >= 0 && percentY < 10) {
        this.isActiveColor0 = true;
        this.isActiveColor1 = false;
      }
      if (percentY >= 10 && percentY < 20) {
        this.isActiveColor0 = false;
        this.isActiveColor1 = true;
        this.isActiveColor2 = false;
      }
      if (percentY >= 20 && percentY < 30) {
        this.isActiveColor1 = false;
        this.isActiveColor2 = true;
        this.isActiveColor3 = false;
      }
      if (percentY >= 30 && percentY < 40) {
        this.isActiveColor2 = false;
        this.isActiveColor3 = true;
        this.isActiveColor4 = false;
      }
      if (percentY >= 40 && percentY < 50) {
        this.isActiveColor3 = false;
        this.isActiveColor4 = true;
        this.isActiveColor5 = false;
      }
      if (percentY >= 50 && percentY < 60) {
        this.isActiveColor4 = false;
        this.isActiveColor5 = true;
        this.isActiveColor6 = false;
      }
      if (percentY >= 60 && percentY < 70) {
        this.isActiveColor5 = false;
        this.isActiveColor6 = true;
        this.isActiveColor7 = false;
      }
      if (percentY >= 70 && percentY < 80) {
        this.isActiveColor6 = false;
        this.isActiveColor7 = true;
        this.isActiveColor8 = false;
      }
      if (percentY >= 80 && percentY < 90) {
        this.isActiveColor7 = false;
        this.isActiveColor8 = true;
        this.isActiveColor9 = false;
      }
      if (percentY >= 90) {
        this.isActiveColor8 = false;
        this.isActiveColor9 = true;
      }
    },
  },
});
</script>

<style lang="scss" scoped>
.menu-column {
  border-right: solid 0.5px #0000001a;
  width: 300px;
  position: fixed;
  top: 50px;
  left: 0;
  overflow: auto;
  height: 100vh;
}
.content-column {
  padding: 0 200px 0 310px;
}
.funy-scroll-column {
  border-left: solid 0.5px #0000001a;
  width: 200px;
  position: fixed;
  top: 50px;
  right: 0;
  overflow: auto;
  height: 100vh;
  font-size: 24px;
}
.getColor {
  background: #ff008070;
  color: #000000a3;
}
</style>
