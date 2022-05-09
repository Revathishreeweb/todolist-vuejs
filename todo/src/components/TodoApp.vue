<template>
  <div class="container" style="max-width: 700px">
    <!----- heading start ------>
    <h2 class="text-center">TodoApp</h2>

    <!--- input ------>
    <div class="d-flex mt-4">
      <input
        type="text"
        v-model="task"
        placeholder="Enter task"
        class="w-100 form-control"
      />
      <button @click="submitTask" class="btn btn-primary rounded-0">
        Submit
      </button>
    </div>

    <!----Task table---->
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th>Task</th>
          <th style="width: 120px">Status</th>
          <th class="text-center">Edit</th>
          <th class="text-center">Delete</th>
        </tr>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>
            <span :class="{'finished': task.status === 'finished'}">
            {{ task.name }} </span>
          </td>
          <td>
            <span @click="changeStatus(index)" class="pointer"
            :class="{'text-danger' :task.status === 'to-do',
            'text-warning' :task.status === 'in-progress',
            'text-success' :task.status === 'finished'
            }"
            >
              {{ firstCharUpper(task.status) }}
            </span>
          </td>
          <td>
            <div>
              <span class="fa fa-pen" @click="editTask(index)"></span>
            </div>
          </td>
          <td>
            <div>
              <span class="fa fa-trash" @click="deleteTask(index)"></span>
            </div>
          </td>
        </tr>
      </thead>
    </table>
  </div>
</template>

<script>
export default {
  name: "TodoApp",
  data() {
    return {
      task: "",
      editedTask: null,
      availableStatus : ["to-do", "in-progress", "finished"],
      tasks: [
        {
          name: "webcode camp",
          status: "to-do",
        },
        {
          name: "Subscribe now",
          status: "in-progress",
        },
        {
          name: "Create youtube videos",
          status: "finished",
        },
      ],
    };
  },
  methods: {
    submitTask() {
      //console.log("Hello world")
      //console.log(this.task)
      if (this.task.length === 0) return;

      if (this.editedTask === null) {
        this.tasks.push({
          name: this.task,
          status: "to-do",
        });
      } 
      else {
        this.tasks[this.editedTask].name = this.task;
        console.log(this.tasks[this.editedTask].name)
        this.editedTask = null;
      }

      this.task = "";
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    editTask(index) {
      this.task = this.tasks[index].name;
      console.log(this.task);
      this.editedTask = index;
    },

    changeStatus(index) {
      let newIndex = this.availableStatus.indexOf(this.tasks[index].status);
      if(++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.availableStatus[newIndex];
    },

    firstCharUpper(str) {
      return str.charAt(0).toUpperCase() + str.slice(1);
    }
  },
};
</script>

<style>
.pointer {
  cursor: pointer;
}

.finished {
  text-decoration: line-through;
}
</style>
