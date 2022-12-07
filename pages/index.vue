<template>
  <main>
    <h1>My TODO list for the day</h1>
    <p>I will add my todo items first thing every morning and I will delete it or click done once
    I've done that task.</p>

    <div class="create-new">
      <input type="text"
      v-model="newTask"
      placeholder="Add a new task"
      @keypress.enter="addTask" />

      <button @click="addTask">Add</button>
    </div>

    <div class="tasks">
      <Task
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task" />
    </div>


  </main>
</template>

<script>
export default {
  data (){
    return {
    newTask: ''
    }
  },
  methods: {
    addTask () {
      if (this.newTask)
        this.$store.commit('ADD_TASK', this.newTask)
        this.newTask = '';
      }
    }
}
</script>
