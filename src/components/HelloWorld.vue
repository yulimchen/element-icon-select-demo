<template>
  <div class="hello">
    <el-input v-model="form.icon" placeholder="请选择图标" />
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      form: {
        icon: ''
      }
    }
  }
}
</script>

<style scoped>
.hello {
  width: 500px;
  margin: 0 auto;
}
</style>
