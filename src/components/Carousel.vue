<template>
  <div>
    <div class="card-carousel">
      <ArrowButton
        arrowType="left"
        @click.native="showPrevElement"
        :disabled="this.reachedMaxLeft"
      />
      <div v-for="(key,index) in requestSlide" :key="index">
        {{index}}
      <Card
        class="current-element"
        :headline="this.howIndex(index).headline"
        :text="this.howIndex(index).text"
        :imgName="this.howIndex(index).imgName"
      />
      </div>
      <ArrowButton
        arrowType="right"
        @click.native="showNextElement"
        :disabled="this.reachedMaxRight"
      />
    </div>
    <Indicators
      :elements="this.cards"
      :currentElementIndex="this.currentElementIndex"
      :showElement="this.showElement"
    />
  </div>
</template>
<script>
import Card from "./Card.vue";
import ArrowButton from "./ArrowButton.vue";
import Indicators from "./Indicators.vue";

export default {
  name: "Carousel",
  props: { cards: Array ,requestSlide:Number},
  components: { Card, ArrowButton, Indicators },

  data() {
    return {
      currentElementIndex: 0,
    };
  },
  computed: {
    howIndex(index){
      if (index < 0) {
        return this.cards[this.cards.length-1]
      }
      if (index > this.cards.length -1) {
        return this.cards[0]
      }
    },
    currentElement() {
      return this.cards[this.currentElementIndex];
    },
    reachedMaxLeft() {
      return this.currentElementIndex === 0;
    },
    reachedMaxRight() {
      return this.currentElementIndex === this.cards.length - 1;
    }
  },
  methods: {
    showNextElement() {
      this.currentElementIndex++;
    },
    showPrevElement() {
      this.currentElementIndex--;
    },
    showElement(elementIndex) {
      this.currentElementIndex = elementIndex;
    }
  }
};
</script>

<style src="../assets/styles/Carousel.css" scoped/>