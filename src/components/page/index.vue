<template>
    <div :class="className">
        <slot></slot>
    </div>
</template>

<script>
export default {
  props:{
    className:{
      type:String,
      default(){
        return 'page'
      }
    }
  },
}
</script>
<style>
.page{
	 position:absolute;
  left:0;
  right:0;
  top:0;
}
body{
  background-color: #eee
}
.fa{
 color: #4D93E4;
}
.weui-tab {
    position: unset;
}
</style>

