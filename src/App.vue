<template>
  <div id="app">
    <header>
      <img
        src="./assets/logo.png"
        alt="Vue.js PWA"
      >
      <span>carousel for other product</span>
    </header>
    <main>
      <h1>{{ headline }}</h1>
      <div class="section">
        <h2>{{this.sections[0].headline}}</h2>
        <Carousel :cards="cards" :requestSlide="requestSlide" />
      </div>
      <div class="section">
        <h2>{{this.sections[1].headline}}</h2>
      </div>
    </main>
  </div>
</template>

<script>
import Carousel from "./components/Carousel";
export default {
  name: "app",
  components: {
    Carousel
  },
  data() {
    return {
      headline:
        "taking position for new!",
      sections: [
        { headline: "taking position for?" },
        {
          headline: "let's make it loud?"
        }
      ],
      cards: [
        {
          headline: "Makes App available Offline",
          text:
            "ini pertama",
          imgName: "setting.svg"
        },
        {
          headline: "Use background sync to defer actions",
          text:
            "ini kedua",
          imgName: "cloud.svg"
        },
        {
          headline: "Send Push Notifications",
          text:
            "ini ketiga",
          imgName: "antenna.svg"
        },
        {
          headline: "Makes App available Offline",
          text:
            "ini keempat",
          imgName: "setting.svg"
        },
        {
          headline: "Use background sync to defer actions",
          text:
            "ini kelima",
          imgName: "cloud.svg"
        },
        {
          headline: "Send Push Notifications",
          text:
            "ini keenam",
          imgName: "antenna.svg"
        }
      ],
      requestSlide:3
    };
  }
};
</script>

<style src="./assets/styles/App.css"/>


