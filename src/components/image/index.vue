<template>
      <div>
        <div v-for="(item,index) in list" :key="index" :class="item.class">
          <div @click='_action(item.onClick,item.param)' data-param="111" >
            <span style="font-size:20px;height:100px"></span>
            <x-img :src="item.src" :defaultSrc="defaultSrc"  @on-success="success" @on-error="error" class="ximg-demo" error-class="ximg-error" :offset="-100" container="#vux_view_box_body"></x-img>
          </div>
        </div>
      </div>
</template>

<script>
const XImg =  require("vux/src/components/x-img/index.vue");

export default {
  props: {
    list: Array,
    defaultSrc: {
      type: String,
      default: 'data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iMzc1cHgiIGhlaWdodD0iMTQwcHgiIHZpZXdCb3g9IjAgMCAzNzUgMTQwIiB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHN0eWxlPSJiYWNrZ3JvdW5kOiAjZWVlZWVlOyI+CiAgICA8IS0tIEdlbmVyYXRvcjogU2tldGNoIDQ3ICg0NTM5NikgLSBodHRwOi8vd3d3LmJvaGVtaWFuY29kaW5nLmNvbS9za2V0Y2ggLS0+CiAgICA8dGl0bGU+QXJ0Ym9hcmQ8L3RpdGxlPgogICAgPGRlc2M+Q3JlYXRlZCB3aXRoIFNrZXRjaC48L2Rlc2M+CiAgICA8ZGVmcz48L2RlZnM+CiAgICA8ZyBpZD0iUGFnZS0xIiBzdHJva2U9Im5vbmUiIHN0cm9rZS13aWR0aD0iMSIgZmlsbD0ibm9uZSIgZmlsbC1ydWxlPSJldmVub2RkIj4KICAgICAgICA8ZyBpZD0iQXJ0Ym9hcmQiIGZpbGw9IiNhY2FjYWMiPgogICAgICAgICAgICA8cGF0aCBkPSJNMjE5LjUsMTA2IEwxNTYuNSwxMDYgQzE1NC4wMTYsMTA2IDE1MiwxMDMuOTg0IDE1MiwxMDEuNSBMMTUyLDM4LjQ5NyBDMTUyLDM2LjAxMyAxNTQuMDE2LDM0IDE1Ni41LDM0IEwyMTkuNSwzNCBDMjIxLjk4NywzNCAyMjQsMzYuMDEzIDIyNCwzOC40OTcgTDIyNCwxMDEuNSBDMjI0LDEwMy45ODQgMjIxLjk4NywxMDYgMjE5LjUsMTA2IEwyMTkuNSwxMDYgWiBNMjE4LDM5Ljk5NyBMMTU4LDM5Ljk5NyBMMTU4LDg4IEwyMTgsODggTDIxOCwzOS45OTcgTDIxOCwzOS45OTcgWiBNMTcxLjUsNDUuOTk3IEMxNzUuNjQzLDQ1Ljk5NyAxNzksNDkuMzU3IDE3OSw1My40OTcgQzE3OSw1Ny42NDMgMTc1LjY0Myw2MSAxNzEuNSw2MSBDMTY3LjM1Nyw2MSAxNjQsNTcuNjQzIDE2NCw1My40OTcgQzE2NCw0OS4zNTcgMTY3LjM1Nyw0NS45OTcgMTcxLjUsNDUuOTk3IEwxNzEuNSw0NS45OTcgWiBNMTg0LjM4OCw3My4xODMgTDE5NS41LDU1IEwyMTIsODIgTDE5MSw4MiBMMTc5LDgyIEwxNjQsODIgTDE3Ny41LDY0IEwxODQuMzg4LDczLjE4MyBMMTg0LjM4OCw3My4xODMgWiIgaWQ9IlBob3RvLUljb24iPjwvcGF0aD4KICAgICAgICA8L2c+CiAgICA8L2c+Cjwvc3ZnPg=='
    },
  },
  components: {
    XImg
  },
  methods:{
     success (src, ele) {
      const span = ele.parentNode.querySelector('span')
      ele.parentNode.removeChild(span)
    },
    error (src, ele, msg) {
      const span = ele.parentNode.querySelector('span')
      span.innerText = 'load error'
    },
    _action(action,param){
      action?action(param):null;
    }
  }
}
</script>

<style scoped lang="less">
.ximg-demo {
  width: 100%;
  height: auto;
}
.ximg-error {
  background-color: yellow;
}
.ximg-error:after {
  content: '加载失败';
  color: red;
}
</style>