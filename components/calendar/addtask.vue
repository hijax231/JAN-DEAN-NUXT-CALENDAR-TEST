<template>
  <div class="taskcontainer">
    <div class="task header">
      <form>
        <input
          class="inputtitle"
          v-model="title"
          type="text"
          placeholder="Add task here.."
        />
        <button class="btnsave" type="submit">Save</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
};
</script>

<style>
.inputtitle {
  padding: 10px;
}

.taskcontainer {
  margin: 0 auto;
  width: 90%;
  background: #e8e8e8;
  box-shadow: 5px 10px black;
  display: grid;
}
.btnsave {
  background-color: grey;
  color: white;
  padding: 10px;
}
</style>