<template>
  <div class="row border rounded p-1 mt-2">
    <div class="col-7 mx-auto d-flex align-items-center">{{ t }}</div>
    <div class="col-2 mx-auto">
      <div class="input-group">
        <button class="btn btn-info" v-if="!done" @click="$emit('doneTodo',k)"><small>done</small></button>
        <button class="btn btn-warning" v-if="done" @click="$emit('undoneTodo',k)"><small>undone</small></button>
      </div>
    </div>
    <div class="col-2 mx-auto">
      <div class="input-group">
        <div class="input-group">
          <button class="btn btn-danger" @click="$emit('deleteTodo',k)"><small>delete</small></button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  emits: ['deleteTodo','doneTodo','undoneTodo'],
  props: ['t', 'done', 'k']
}
</script>

<style scoped>

</style>