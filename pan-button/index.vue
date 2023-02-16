<template>
  <button
    class="pan-button"
    :style="getStyle(color,backgroundColor)" 
    :class="[
      `pan-button-${type}`,
      {
        'is-disabled': disabled,
        'is-plain': plain,
        'is-round': round,
        'is-circle': circle,
      },
    ]"
    :disabled="disabled"
    @click="handleClick"
  >
    <span>
      <slot></slot>
    </span>
  </button>
</template>

<script setup lang="ts">
import { defineProps,defineEmits } from "vue";
let myEmit = defineEmits(["myclick"])

const props = defineProps({
  type: {
    type: String,
    default: "default",
  },
  plain: {
    type: Boolean,
    default: false,
  },
  round: {
    type: Boolean,
    default: false,
  },
  circle: {
    type: Boolean,
    default: false,
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  color:{
    type:String,
  } ,
  backgroundColor:{
    type:String,
  }
});

const handleClick = (e:any) => {
  myEmit('myclick',e);
};

const getStyle = (color:String|undefined,backgroundColor:String|undefined) =>{
  let str=""
  if(color){
    str+="color:"+color+";"
  }
  if(backgroundColor){
    str+="background-color:"+backgroundColor+";"
  }
  return str
}

</script>

<style lang="less" scoped>
.pan-button {
  display: inline-flex; //变成行内块
  justify-content: center;
  align-items: center;
  line-height: 1;
  height: 32px;
  white-space: nowrap;
  cursor: pointer;
  text-align: center;
  outline: 0;
  transition: 0.1s;
  vertical-align: middle;
  padding: 8px 15px;
  font-size: 14px;
  background: #ffffff;
  border: 1px solid #dcdfe6;
  border-radius: 5px;
  margin-left: 10px;

  -webkit-appearance: none;
  /*去除谷歌浏览器自带按钮样式：*/
  box-sizing: border-box;
  /*内边距和边框放入宽高内*/
  outline: none;
  /*去除按钮自带边框*/
  transition: 0.1s;

  //禁止元素的文字被选中
  -moz-user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;

  &:hover,
  &:focus {
    color: #409eff;
    background-color: #e7f1fa;
    border-color: #c6e2ff;
  }
}

.pan-button-primary {
  color: #fff;
  background-color: #409eff;
  border-color: #409eff;

  &:hover,
  &:focus {
    background: #66b1ff;
    background-color: #66b1ff;
    color: #fff;
  }
}

.pan-button-success {
  color: #fff;
  background-color: #67c23a;
  border-color: #67c23a;

  &:hover,
  &:focus {
    background: #85ce61;
    background-color: #85ce61;
    color: #fff;
  }
}

.pan-button-info {
  color: #fff;
  background-color: #909399;
  border-color: #909399;

  &:hover,
  &:focus {
    background: #a6a9ad;
    background-color: #a6a9ad;
    color: #fff;
  }
}

.pan-button-warning {
  color: #fff;
  background-color: #e6a23c;
  border-color: #e6a23c;

  &:hover,
  &:focus {
    background: #ebb563;
    background-color: #ebb563;
    color: #fff;
  }
}

.pan-button-danger {
  color: #fff;
  background-color: #f56c6c;
  border-color: #f56c6c;

  &:hover,
  &:focus {
    background: #f78989;
    background-color: #f78989;
    color: #fff;
  }
}

// 朴素按钮样式
.pan-button.is-plain {
  &:hover,
  &:focus {
    background: #fff;
    border-color: #489eff;
    color: #409eff;
  }
}

.pan-button-primary.is-plain {
  color: #409eff;
  background: #ecf5ff;

  &:hover,
  &:focus {
    background: #409eff;
    border-color: #409eff;
    color: #fff;
  }
}

.pan-button-success.is-plain {
  color: #67c23a;
  background: #c2e7b0;

  &:hover,
  &:focus {
    background: #67c23a;
    border-color: #67c23a;
    color: #fff;
  }
}

.pan-button-info.is-plain {
  color: #909399;
  background: #d3d4d6;

  &:hover,
  &:focus {
    background: #909399;
    border-color: #909399;
    color: #fff;
  }
}

.pan-button-warning.is-plain {
  color: #e6a23c;
  background: #f5dab1;

  &:hover,
  &:focus {
    background: #e6a23c;
    border-color: #e6a23c;
    color: #fff;
  }
}

.pan-button-danger.is-plain {
  color: #f56c6c;
  background: #fbc4c4;

  &:hover,
  &:focus {
    background: #f56c6c;
    border-color: #f56c6c;
    color: #fff;
  }
}

// round
.pan-button.is-round {
  border-radius: 20px;
  padding: 12px 23px;
}

// circle
.pan-button.is-circle {
  border-radius: 50%;
  padding: 12px;
}

.pan-button.is-disabled {
  cursor: no-drop;
}

.pan-button.pan-color{
  color: var(color);
}
</style>
>
