<template>
  <section class="main__container contact" id="contact" :class="{ show: show }">
    <h2 class="main__container__title">
      <p class="main__container__title--en">Contact</p>
      <p class="main__container__title--ja">お問い合わせ</p>
    </h2>
  </section>
</template>

<script>
export default {
  name: "Contact",
  data() {
    return {
      show: false,
    };
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      if (!this.show) {
        var top = this.$el.getBoundingClientRect().top;
        this.show = top < window.innerHeight - 150;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/import";
</style>
