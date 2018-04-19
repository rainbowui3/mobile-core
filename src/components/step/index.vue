<template>
      <div>
        <flow v-if='type=="primary"' :orientation="vertical?'vertical':''"  v-bind:style="styles">
            <template v-for="(item, index) in data">
                 <flow-state v-bind:key="`s${index}`" :state="index+1" :title="item.title" :is-done="item.isDone" ></flow-state>
                 <flow-line v-bind:key="`${index}`" :is-done="!item.process && item.isDone" :line-span='item.lineSpan' :tip="item.tip"   :tip-direction="vertical?'right':'top'" :process-span="item.process" ></flow-line>
            </template>
        </flow>
      </div>
</template>

<script>
//const Step =  require("vux/src/components/step/step.vue");
//const StepItem =  require("vux/src/components/step/step-item.vue");
const Flow =  require("vux/src/components/flow/flow.vue");
const FlowState =  require("vux/src/components/flow/flow-state.vue");
const FlowLine =  require("vux/src/components/flow/flow-line.vue");

export default {
  props: {
    step: Number,
    data:Array,
    type:{
        type:String,
        default(){
          return 'primary'
        }
    },
    vertical:Boolean,
    styles:String
  },
  components: {
    Flow,
    FlowState,
    FlowLine
  },
  data(){
    return {
      tempModel:this.step,
    }
  },
  watch:{
    step(val){
      this.tempModel= val;
    },
    tempModel(val){
      this.onChange?this.onChange(val):null;
    }
  },
}
</script>