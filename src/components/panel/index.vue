<template>
    <div>
         <panel  :list="data" :type="type" @on-img-error="onImgError"></panel>
    </div>
</template>

<script>
const Panel =  require("vux/src/components/panel/index.vue");

export default {
  props:{
    data:Array,
    type:{
      type:String,
      default(){
        return '2'
      }
    }
  },
  components: {
    Panel
  },
  methods:{
      onImgError(){
        console.error('image load error')
      }
  }
}
</script>
 


