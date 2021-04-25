<template>
  <div class="hello">
    <!-- readonly, shallowReadonly -->
    <div @click="update()">
      <p>{{ a }}</p>
      <p>{{ b }}</p>
    </div>
  </div>
</template>

<script>
import { reactive, readonly, shallowReadonly, toRefs } from "vue";
export default {
  name: "readonly",
  setup() {
    const state = reactive({
      a: 1,
      b: {
        c: 2,
      },
    });

    const m = readonly(state);
    const m2 = shallowReadonly(state);

    const update = () => {
      m.a++; //无法修改 只读
      m2.a++; //无法修改
      m2.b.c++; //可以修改 视图层数据改变
    };

    return {
      ...toRefs(state),
      update,
    };
  },
};
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
