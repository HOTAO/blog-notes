<template>
  <div>
    <h1>vue添加数据视图不更新问题</h1>
    <ul>
      <li v-for="(vItem, key) in vueData" :key="key">{{ vItem }}</li>
    </ul>
  </div>
</template>

<script>
const jsData = {
  ja: "张三",
  jb: "李四"
}

export default {
  data() {
    return {
      vueData: {
        va: "张三",
        vb: "李四"
      }
    }
  },
  mounted() {
    console.log(jsData, this.vueData);
    this.notAllow()
    // this.allow()
  },
  methods: {
    notAllow() {
      // demo 1
      this.vueData.newKeyA = "keyA";
      console.log(this.vueData);

      // demo 2
      // Object.assign(this.vueData, { newKeyA: "keyA" });
      // console.log(this.vueData);

      // demo 3
      // this.vueData = Object.assign(this.vueData, { newKeyA: "keyA" });
      // console.log(this.vueData);
    },
    allow() {
      // demo 1
      this.vueData = {
        ...this.vueData,
        newKeyA: "keyA"
      }
      console.log(this.vueData);

      // demo 2
      // this.$set(this.vueData, "newKeyA", "keyA");
      // console.log(this.vueData);
    }
  }
}
</script>
