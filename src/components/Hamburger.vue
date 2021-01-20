<template>
  <div class="hamburger" @click="toggle" :class="{ active: isActive }">
    <span class="bar first"></span>
    <span class="bar second"></span>
    <span class="bar third"></span>
  </div>
</template>

<script>
export default {
  name: "Hamburger",
  methods: {
    toggle() {
      this.$parent.isActiveMenu = !this.$parent.isActiveMenu;
    },
  },
  props: {
    isActive: Boolean,
  },
};
</script>

<style lang="scss">
@import "@/assets/scss/import";
@import "@/assets/scss/reset";

.hamburger {
  position: fixed;
  top: 24px;
  right: 24px;
  z-index: 5000;
  width: 40px;
  height: 40px;
  cursor: pointer;
  background: $transparent-black;
  border-radius: 4px;
  transition: 0.3s;

  @include mq("pc") {
    &:hover {
      background: $transparent-black-hover;
    }
  }

  .bar {
    position: relative;
    top: 5px;
    display: block;
    width: 24px;
    height: 2px;
    margin: 6px auto;
    background: $off-white;
    transition: 0.2s ease-out;
  }

  &.active {
    .first {
      transform: translateY(8px) rotate(-315deg) scale(1.1);
    }

    .second {
      opacity: 0;
    }

    .third {
      transform: translateY(-8px) rotate(315deg) scale(1.1);
    }
  }
}
</style>
