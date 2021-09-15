<template>
  <div class="row">
    <div class="col-4 mx-auto my-4">
      To get started,add some items to your list
    </div>
  </div>
  <div class="row">
    <div class="col-4 mx-auto">
      <div class="row">
        <div class="col-8">
          <div class="input-group mb-3">
            <input type="text" v-model="input" placeholder="Write todo" class="form-control col-8">
          </div>
        </div>
        <div class="col-4">
          <div class="input-group mb-3">
            <button class="btn btn-info" @click="addTodo">add</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddToDo",
  emits:['addToDo'],
  data(){
    return{
      input:''
    }
  },
  methods:{
    addTodo(){
      this.$emit('addToDo',this.input);
      this.input=''
    }

  }

}
</script>

<style>

</style>