<template>
  <div
    :class="open ? 'accordion__item--open' : 'accordion__item'"
    @click="() => changeOpen(this.index)"
  >
    <button class="accordion__item__title">{{ accordion__item.title }}</button>
    <div class="accordion__item--hidden">
      <p>{{ accordion__item.content }}</p>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";

export default {
  name: "AccordionItem",
  props: ["accordion__item", "index", "open", "activeIndex"],
  computed: {
    ...mapGetters("accordionBorchenko", [
      "getAccordion"
    ]),
  },
  methods: {
    ...mapActions("accordionBorchenko", [
      "changeOpen", 
      "setActiveIndex"
    ]),
  },
  mounted() {
    if (this.open === false && this.activeIndex == this.index) {
      this.changeOpen(this.index);
    }
  },
};
</script>

<style scoped lang="less">
@import "styles/styles.less";
</style>