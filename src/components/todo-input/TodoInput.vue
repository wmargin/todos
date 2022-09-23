<template>
  <form action="" class="form-inline" @submit.prevent="onFormSubmit">
    <div class="input-group mb-2 mr-sm-2">
      <div class="input-group-prepend">
        <div class="input-group-text">任务</div>
      </div>

      <input
        type="text"
        class="form-control"
        placeholder="请填写任务信息"
        style="width: 356px"
        v-model.trim="taskname"
      />
    </div>

    <button type="submit" class="btn btn-primary mb-2">添加任务</button>
  </form>
</template>

<script>
export default {
  name: "TodoInput",
  data() {
    return {
      taskname: "",
    }
  },
  methods: {
    onFormSubmit() {
      if (!this.taskname) return alert("任务不能为空！")
      // 触发自定义的add事件，并向外界传递数据
      this.$emit("add", this.taskname)
      // 清空文本
      this.taskname = ""
    },
  },
  emits: ["add"],
}
</script>

<style lang="scss" scoped></style>
