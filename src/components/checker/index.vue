<template>
      <div>
        <checker v-if="type=='default'"  v-model="model[value]" :max="max" :type="_multiple" default-item-class="item" selected-item-class="item-selected"  @on-change="_onChange" >
           <checker-item :disabled="item.disabled" :value="modelKey?item:item.key" v-for="(item, index) in data" :key="index">{{item.value}}</checker-item>
        </checker>
        <check-icon v-if="type=='icon'" @on-change="_onChange" :value.sync="model[value]"  :type="plain?'plain':undefined">{{ text }}</check-icon>
        <checklist v-if="type=='list'" @on-change="_onChange" :max="max" :disabled="disabled" :title="title" :label-position="labelPosition" :required="required" :options="data" v-model="model[value]"></checklist>
      </div>
</template>

<script>
const Checker =  require("vux/src/components/checker/checker.vue");
const CheckerItem =  require("vux/src/components/checker/checker-item.vue");
const CheckIcon =  require("vux/src/components/check-icon/index.vue");
const Checklist =  require("vux/src/components/checklist/index.vue");

export default {
  props: {
    model: [String, Number, Array,Boolean, Object],
    value:String,
    data:Array,
    onChange:Function,
    modelKey:Boolean,
    required:Boolean,
    disabled:Boolean,
    plain:Boolean,
    type:{
        type:String,
        default(){
            return 'list'
        }
    },
    labelPosition:{
        type:String,
        default(){
            return 'right'
        }
    },
    text:String,
    title:String,
    max:Number,
    multiple:Boolean
  },
  components: {
    Checker,
    CheckerItem,
    CheckIcon,
    Checklist
  },
  computed:{
      _multiple(){
          return this.multiple?"checkbox":undefined
      },
      _onChange(){
          return this.onChange?this.onChange:()=>{};
      }
  },
}
</script>
