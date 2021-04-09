<!--
 * @Author: atdow
 * @Date: 2021-04-09 16:33:41
 * @LastEditors: null
 * @LastEditTime: 2021-04-09 16:51:20
 * @Description: file content
-->
<template>
  <router-view></router-view>
</template>

<script>
import Vue from 'vue'

export default {
  created () {
    this.loadLanguage()
  },
  methods: {
    loadLanguage () {
      if (this.$route.params.lang == 'zh-CN') {
        Vue.config.lang = 'zh-CN'
        localStorage.setItem('language', 'zh-CN')
      } else if (this.$route.params.lang == 'en-US') {
        Vue.config.lang = 'en-US'
        localStorage.setItem('language', 'en-US')
      } else {
        this.$router.replace({name: this.$route.name, params: {lang: navigator.language == 'zh-CN' ? 'zh-CN' : 'en-US'}})
      }
    }
  },
  watch: {
    '$route.params.lang': function (val) {
      this.loadLanguage()
    }
  }
}
</script>
