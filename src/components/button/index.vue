<template>
  <x-button 
    :gradients="gradients" 
    :type="_type" :link="link" 
    :show-loading="loading" 
    :mini="mini" 
    :plain="plain" 
    :style="styleClass" 
    :class="className" 
    :disabled="disabled"
    @click.native="clickButton"
    v-bind:data-param="param"
    ><slot/></x-button>
</template>

<script>
const XButton =  require("vux/src/components/x-button/index.vue");

export default {
  props: {
    gradients: Array,
    value: String,
    type: {
      type:String,
      default(){
        return 'primary'
      }
    },
    link: String,
    styleClass: String,
    className: String,
    loading:Boolean,
    mini:Boolean,
    plain:Boolean,
    disabled:Boolean,
    onClick:Function,
    param:String
  },
  components: {
    XButton
  },
  computed:{
    _type(){
      return this.type=="danger"?'warn':this.type;
    },
  },
  methods:{
    clickButton(event){
        const checkResult = [];
        this.checkInput(this.$root,checkResult);
        if(!_.isEmpty(checkResult)){
            const errorObj = checkResult[0];
            errorObj.focus();
            errorObj.blur();
            errorObj.focus();
        }else{
           this.onClick?this.onClick(event):null;
        }
    },
    checkInput(obj,inputs){
        if(obj&&!_.isEmpty(obj.$refs)){
          _.each(obj.$refs,(ref)=>{
              if(obj.hasErrors){
                  inputs.push(obj)
              }
              if(obj.required&&_.isEmpty(obj.value)){
                  inputs.push(obj)
              }
          });
        }
        _.each(obj.$children,(children)=>{
            this.checkInput(children,inputs);
        })
    } 
  }
}
</script>
<style>
.weui-btn_primary {
    background-color: #409EFF!important;
}
.weui-btn_loading.weui-btn_primary {
    background-color: #409EFF!important;
}
.weui-btn_plain-primary {
    color: #409EFF;
    border: 1px solid #409EFF!important;
}
.weui-btn_disabled.weui-btn_primary {
    background-color: #409EFF!important;
}

</style>
