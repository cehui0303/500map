<template>
  <div
    ref="card_radio"
    class="card"
    :style="{borderColor: touching || selected ? borderColor : 'white'}"
    @mouseover="handleMouseover"
    @mouseleave="handleMouseleave"
    @click="handleClick"
  >
    <slot />
    <div v-show="selected" class="mark">
      <div class="bg" :style="{ borderTopColor: borderColor }" />
      <div class="icon"><Icon type="md-done-all" /></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MakeSelectable',
  props: {
    /**
     * 边框颜色
     */
    borderColor: {
      type: String,
      default: '#2d8cf0'
    },
    selected: Boolean
  },
  data() {
    return {
      touching: false
    }
  },
  methods: {
    handleClick() {},
    handleMouseover() {
      this.touching = true
    },
    handleMouseleave() {
      this.touching = false
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  cursor: pointer;
  border-color: white;
  border-width: 4px;
  border-style: solid;
  width: 100%;
  overflow: hidden;
  padding: 1px;
  position: relative;
  .mark {
    position: absolute;
    right: 0;
    top: 0;
    $height: 40px;
    width: $height;
    height: $height;
    .bg {
      width: 0;
      height: 0;
      border-top: $height solid transparent;
      border-left: $height solid transparent;
    }
    .icon {
      position: absolute;
      top: 0;
      right: 0;
      width: $height / 2;
      height: $height / 2;
      color: white;
      font-weight: bold;
    }
  }
}
</style>
