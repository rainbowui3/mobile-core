<template>
    <div>
      <view-box ref="viewBox">
        <slot></slot>
      </view-box>
    </div>
</template>

<script>
const ViewBox =  require("vux/src/components/view-box/index.vue");

export default {
  components: {
    ViewBox
  },
}
</script>