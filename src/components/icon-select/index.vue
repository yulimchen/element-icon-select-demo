<template>
  <div class="icon-select-body">
    <el-input
      v-model="name"
      clearable
      placeholder="请输入图标名称搜索"
      @clear="filterIcons"
      @input.native="filterIcons"
    >
      <i slot="suffix" class="el-icon-search el-input__icon" />
    </el-input>
    <div class="icon-select-list">
      <div 
        v-for="(item, index) in iconList" 
        :key="index" 
        @click="selectedIcon(item)"
      >
        <icon :name="item" />
        <span>{{ item }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import icons from './icon-list'
import icon from '../icon'

export default {
  name: 'IconSelect',
  components: {
    icon
  },
  data() {
    return {
      name: '',
      iconList: icons
    }
  },
  methods: {
    filterIcons() {
      this.iconList = icons
      if (this.name) {
        this.iconList = this.iconList.filter(item => item.includes(this.name))
      }
    },
    selectedIcon(name) {
      this.$emit('selected', name)
      // 触发关闭 el-popover
      document.body.click()
    },
    reset() {
      this.name = ''
      this.iconList = icons
    }
  }
}
</script>

<style lang="scss" scoped>
  .icon-select-body {
    padding: 10px;

    .icon-select-list {
      height: 200px;
      overflow-y: scroll;
      margin-top: 12px;

      // 滚动条
      &::-webkit-scrollbar-thumb {
        background-color: #ccc;
        outline-offset: -2px;
        outline: 1px solid #ccc;
        border-radius: 6px;
        border: 1px solid #ccc;
      }
      &::-webkit-scrollbar {
        width: 10px;
        background-color: rgba(#ccc, 0.2);
        border-radius: 6px;
      }

      div {
        height: 36px;
        margin-bottom: -2px;
        cursor: pointer;
        width: 33%;
        float: left;
        display: flex;
        align-items: center;

        span {
          margin-left: 6px;
          font-size: 12px;
        }
      }
    }
  }
</style>
