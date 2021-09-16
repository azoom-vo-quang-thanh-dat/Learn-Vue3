<template>
  <h1>Welcome to {{ company }}</h1>
  <div style="float: left">
    <h4>Setup Function</h4>
    <ul>
      <li>two arguments: <b>props, context</b></li>
      <li>Hàm setup() sẽ được chạy khi các props được cập nhật</li>
      <li>{{ readersNumber }} {{ book.title }}</li>
    </ul>
  </div>
</template>

<script>
import { toRefs } from "vue";
import { h, ref, reactive } from "vue";
export default {
  props: {
    company: String,
  },
  setup(props, context) {
    const { company } = toRefs(props); // sử dụng toRefs để cấu trúc lại props
    console.log(props);
    console.log(company);
    console.log(context.attrs);
    const readersNumber = ref(0);
    const book = reactive({ title: "Vue 3 Guide" });

    // Usage with Templates
    //   return {
    //     readersNumber,
    //     book
    //   }
    return () => h("h1", [readersNumber.value, book.title]); // Usage with Render Functions
  },
};
</script>

<style></style>
