<template>
  <el-button
    v-loading.fullscreen.lock="fullscreenLoading"
    type="primary"
    @click="openFullScreen1"
  >
    As a directive
  </el-button>
  <el-button type="primary" @click="openFullScreen2"> As a service </el-button>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import { ElLoading } from 'element-plus'

export default defineComponent({
  setup() {
    const fullscreenLoading = ref(false)
    const openFullScreen1 = () => {
      fullscreenLoading.value = true
      setTimeout(() => {
        fullscreenLoading.value = false
      }, 2000)
    }

    const openFullScreen2 = () => {
      const loading = ElLoading.service({
        lock: true,
        text: 'Loading',
        spinner: 'el-icon-loading',
        background: 'rgba(0, 0, 0, 0.7)',
      })
      setTimeout(() => {
        loading.close()
      }, 2000)
    }

    return {
      fullscreenLoading,
      openFullScreen1,
      openFullScreen2,
    }
  },
})
</script>
