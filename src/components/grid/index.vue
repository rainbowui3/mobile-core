<template>
<div>
  <grid :cols="cols">
           <grid-item  :label="item.text"  v-for="(item, index) in data"  :key="index" :link="item.link" @on-item-click="onItemClick(item.onClick)">
                 <i slot="icon"  :class="item.icon"><img :src="item.img" v-if="item.img"/></i>
           </grid-item>
  </grid>
</div> 
</template>

<script>
const Grid =  require("vux/src/components/grid/grid.vue");
const GridItem =  require("vux/src/components/grid/grid-item.vue");

export default {
  props: {
    cols: {
      type: Number,
      default () {
        return 4
      }
    },
    data: Array
  },
  components: {
    Grid,
    GridItem
  },
  computed: {
  },
  methods: {
    onItemClick (onClick) {
      onClick?onClick():null;
    }
  }
}
</script>
 
