<template>
<div>
      <x-table :cell-bordered="border">
        <thead>
          <tr v-for="(item, index) in data.head" :key="index">
               <th v-for="(hitem, hindex) in item" :key="hindex">
                 {{hitem.text}}
               </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in data.body" :key="index" >
            <td v-for="(citem, cindex) in item" :key="cindex" :colspan="citem.colspan" :rowspan="citem.rowspan">
              <a v-if="citem.link" href="javascript:void(0)" @click="goto(citem.link)">
                <span v-if="citem.icon" :title="citem.text" :class="citem.icon"></span>
                <span v-else-if="citem.text">{{citem.text}}</span>
              </a>
               <a v-else-if="citem.onClick" href="javascript:void(0)" @click="click(citem,item)">
                <span v-if="citem.icon" :title="citem.text" :class="citem.icon"></span>
                <span v-else-if="citem.text">{{citem.text}}</span>
              </a>
              <div v-else-if="citem.text">{{citem.text}}</div>
            </td>
          </tr>
        </tbody>
      </x-table>
</div>    
</template>

<script>
const XTable =  require("vux/src/components/x-table/index.vue");
export default {
  props: {
    data: Object,
    border:Boolean
  },
  components: {
    XTable
  },
  methods:{
    goto(link){
        window.location.hash=link;
    },
    click(citem,item){
        citem.onClick?citem.onClick(citem):()=>{};
    }
  }
}
</script>
 