<template>
  <div class="header">
    <div class="logo" @click="router.push('/')">小🐖骑🐎赏桂❀</div>
    <!-- <div class="logo" @click="router.push('/')">
      <img src="@/assets/logo.jpg" alt="" />
    </div> -->
    <div class="search" v-if="route.fullPath === '/'">
      <a-input
        v-model:value="value"
        class="input_search"
        placeholder=" 🔍  input your search text"
      />
    </div>
    <div class="right">
      <div class="upload" @click="toUpload">
        <PlusCircleOutlined />
      </div>
      <!-- 登录或者个人中心 可以放个组件 -->
      <!-- <div class="person gh_button">登录</div> -->
      <a-button class="person" @click="toPerson">{{ text }}</a-button>
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
import { useRouter, useRoute } from 'vue-router'
import { PlusCircleOutlined } from '@ant-design/icons-vue'
import { message } from 'ant-design-vue'

const router = useRouter()
const route = useRoute()
const value = ref('')
const text = ref('登录')

const login = () => {}
const toUpload = () => {
  router.push('/upload')
}
const toPerson = () => {
  if (text.value === '登录') {
    text.value = '助麻花'
    message.success('登陆成功', 1)
  } else {
    router.push('/person')
  }
}

const onSearch = (searchValue) => {
  console.log('use value', searchValue)
  console.log('or use this.value', value.value)
}
</script>
<style scoped lang="less">
.header {
  display: flex;
  padding: 0.5vw 0;
  box-sizing: border-box;
  justify-content: space-between;

  .logo {
    display: flex;
    align-items: center;
    border-radius: 0.6vw;
    padding: 0 0.8vw;
    cursor: pointer;
    // width: 11vw;
    background-color: gold;
  }
  .logo > img {
    height: 100%;
    object-fit: contain;
  }
  .search {
    display: flex;
    align-items: center;

    .input_search {
      width: 26vw;
      height: 6vh;
      background-color: rgb(251, 243, 229);
    }
  }
  .right {
    display: flex;
    align-items: center;

    .upload {
      margin-right: 1.2vw;
      border-radius: 50%;
      text-align: center;
      line-height: 1.7vw;
      font-size: 2vw;
      background-color: gold;
      color: #222;
      position: relative;
      // 设置字体颜色变化动画
      transition-property: all;
      transition-duration: 0.2s;
    }
    .upload:hover {
      cursor: pointer;
      color: #4096ff;
      box-shadow: 0 0 0.8vw #ccc;
    }

    .person {
      padding: 0 1.2vw;
      background-color: gold;
    }
  }
}
</style>
