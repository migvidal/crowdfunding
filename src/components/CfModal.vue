<template>
  <div
    class="modal-bg"
    @keydown.esc="$emit('modalclose')"
    @keydown.enter="logHasSlot"
    @click="handleBgClick"
    tabindex="0"
  >
    <div class="modal">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "CfModal",
  computed: {
    hasSlot() {
      return !!this.$slots.default;
    },
  },
  methods: {
    handleBgClick(e) {
      //closes modal when bg clicked
      if (e.target.classList.contains("modal-bg")) {
        this.$emit("modalclose");
      }
    },
    logHasSlot() {
      console.log(this.$slots.default);
      return false;
    },
  },
};
</script>

<!-- Unscoped styles -->
<style lang="scss">
.modal-inner {
  padding: 2rem;
}
</style>

<!-- Scoped styles -->
<style lang="scss" scoped>
.modal-bg {
  position: fixed;
  z-index: 100;
  top: 0;
  left: 0;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(0, 0, 0, 0.5);
  overflow: auto;
  .modal {
    position: relative;
    margin: 60px auto;
    width: 90%;
    background-color: white;
    border-radius: $radius;
    overflow: auto;
  }
}
</style>
