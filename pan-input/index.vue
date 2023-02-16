<template>
  <div class="main">
    <input
      class="pan-input"
      v-model="input"
      :class="[{ 'is-disabled': disabled }]"
      :type="type"
      :placeholder="placeholder"
      :disabled="disabled"
    />
    <div v-if="clearable && input" class="clear-box" @click="clearText"></div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const input = ref('')

const props = defineProps({
  placeholder: {
    type: String,
    default: "",
  },
  type: {
    type: String,
    default: "text",
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  clearable: {
    type: Boolean,
    default: false,
  },
});

const clearText =()=>{
    input.value=""
}
</script>

<style lang="less" scoped>

.main{
    width: 100%;
    display: flex;
    position: relative;
}
.pan-input {
  box-sizing: border-box;
  width: 100%;
  line-height: 1;
  height: 32px;
  white-space: nowrap;
  padding: 0;
  outline: 0;
  background: 0 0;
  text-indent: 10px;
  border-radius: 5px;
  font-size: 14px;
  flex-grow: 1;
  border: 1.7px solid#dcdfe6;

  white-space: nowrap;
  //   cursor: pointer;
  /*去除按钮自带边框*/
  transition: 0.1s;
  //禁止元素的文字被选中
  -moz-user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  &:focus {
    border: 2px solid#409eff;
  }
}

.clear-box {
  position: absolute;
  transition: 0.4s cubic-bezier(0.625, 0.045, 0.355, 1);
  width: 16px;
  height: 16px;
  top: 8px;
  right: 8px;
  line-height: 16px;
//   background: #ffffff;
  border-radius: 100%;

  // 画叉的部分
  &::after {
    width: 12px;
    position: absolute;
    height: 1.6px;
    background: rgb(177, 176, 176);
    content: "";
    top: 6.5px;
    left: 3.3px;
    transform: rotate(134deg);
    -ms-transform: rotate(134deg);
    -moz-transform: rotate(134deg);
    -webkit-transform: rotate(134deg);
    -o-transform: rotate(134deg);
  }
  &::before {
    width: 12px;
    position: absolute;
    height: 1.5px;
    background: rgb(177, 176, 176);
    content: "";
    top: 6.5px;
    left: 3.3px;
    transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    -moz-transform: rotate(45deg);
    -webkit-transform: rotate(45deg);
    -o-transform: rotate(45deg);
  }
}

.pan-input.is-disabled {
  cursor: no-drop;
  background-color: #f5f7fa;
}
</style>
