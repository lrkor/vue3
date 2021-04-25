<template>
  <div class="hello">
    <!-- customRef -->
    <div>
      <input v-model="keyword" placeholder="搜索关键字" />
      <p>{{ keyword }}</p>
    </div>
  </div>
</template>

<script>
import { customRef } from "vue";
export default {
  name: "customRef",
  setup() {
    const keyword = useDebouncedRef("", 500);
    console.log(keyword);
    return {
      keyword,
    };
  },
};
function useDebouncedRef(value, delay = 200) {
  let timeout;
  return customRef((track, trigger) => {
    return {
      get() {
        // 告诉Vue追踪数据
        track();
        return value;
      },
      set(newValue) {
        clearTimeout(timeout);
        timeout = setTimeout(() => {
          value = newValue;
          // 告诉Vue去触发界面更新
          trigger();
        }, delay);
      },
    };
  });
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
