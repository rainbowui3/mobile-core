<template>
 <div>
    <popup-radio @on-change="_onChange" :title="title" :readonly="readonly" :options="options" v-model="model[value]"  :placeholder="placeholder" >
              <p slot="popup-header" class="vux-1px-b demo3-slot" v-if="header">{{header}}</p>
    </popup-radio>
</div>
</template>


<script>
const PopupRadio =  require("vux/src/components/popup-radio/index.vue");
export default {
  props: {
    title: String,
    model:Object,
    value:String,
    options:Array,
    header:String,
    readonly:Boolean,
    onChange:Function
  },
  data() {
    return {
      i18n:this.$i18n["messages"],
    };
  },
  components: {
    PopupRadio
  },
  computed:{
      placeholder(){
        return _.isEmpty(this.model[this.value])?this.i18n[this.$i18n["locale"]].vux.common.pleaseselect:null
      },
      _onChange(){
        return this.onChange?this.onChange:()=>{};
      }
  },
  methods:{
      clearValue (value) {
        this.model[this.value] = null;
      }
  },
};
</script>

 
