<template>
  <div class="hello">
    <el-popover
      placement="bottom-start"
      width="475"
      trigger="click"
      @show="$refs['iconSelect'].reset()"
    >
      <icon-select ref="iconSelect" @selected="selectedIcon" />
      <el-input 
        slot="reference" 
        v-model="form.icon" 
        placeholder="点击选择图标" 
        readonly
      >
        <icon
          slot="prefix"
          :name="form.icon"
          style="height: 24px; line-height: 40px; width: 24px;"
        />
      </el-input>
    </el-popover>
  </div>
</template>

<script>
import iconSelect from './icon-select';
import icon from './icon';

export default {
  name: 'Demo',
  components: {
    iconSelect,
    icon
  },
  data() {
    return {
      form: {
        icon: ''
      }
    }
  },
  methods: {
    selectedIcon(name) {
      this.form.icon = name
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
