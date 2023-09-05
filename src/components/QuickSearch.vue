<template>
  <div class="quick-warper">
    <!-- 图标 -->
    <div class="icon">
      <el-select
        v-model="searchEngine"
        class="m-2"
        placeholder="Select"
        size="large"
      >
        <el-option
          v-for="item in searchEngineJson"
          :key="item.name"
          :label="item.name"
          :value="item.link"
        />
      </el-select>
    </div>
    <!-- 搜索组件 -->
    <div class="search">
      <el-input
        v-model="searchInp"
        placeholder="输入关键词搜索 | tab键切换引擎"
        @keyup.enter="handleEnterKey"
      />
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import searchEngineJson from "@/data/engine.json";

const searchInp = ref<string>("");
const searchEngine = ref<string>(searchEngineJson[0].link);

const handleEnterKey = () => {
  const link = searchEngine.value + searchInp.value;
  window.open(link);
};
</script>

<style scoped lang="scss">
.quick-warper {
  display: flex;
  align-items: center;
  width: 300px;

  .icon {
    width: 60px;
  }

  .search {
    flex: 1;
  }
}
</style>
