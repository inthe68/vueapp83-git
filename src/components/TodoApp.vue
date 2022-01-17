<template>
  <div
    class="
      container
      bg-dark
      text-light
      border border-3 border-secondary
      rounded-3
    "
  >
    <div class="mt-1">
      <h2 class="text-center text-light page-custom-heading">
        ListOfThingsToDoToday
      </h2>
    </div>

    <!-- inputs for todo -->
    <div class="d-flex">
      <!-- Make Input and Button Shorter height wise:  -__-  :: style="height:20px;" -->
      <input
        v-model="task"
        type="text"
        placeholder=""
        class="w-75 rounded-3 mx-3 text-dark"
      />
      <button @click="submitTask" class="btn btn-primary text-center mx-3">
        Click To Submit Task
      </button>
    </div>
    <div class="container push mt-3 rounded-3" style="height: 250px">
      <h3>Push content down</h3>
      <p class="page-ui-description rounded-3">
        Ui Description: Add item to todo list 
        - 
        - 
        <span class="ai-achievement"></span>
      </p>
     
    </div>
    <!-- List For Tasks to show up -->
    <table class="table text-light">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col" class="text-center">Edit</th>
          <th scope="col" class="text-center">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>{{ task.name }}</td>
          <td>
            <span @click="changeStatus(index)" class="status pointer">
            {{firstCharUpper(task.status) }}
            </span>
          </td>

          <td>
            <div
              @click="editTask(index)"
              class="
                text-center text-light
                todo-btn
                border border-primary
                rounded-3
                p-1
                page-delete-container
              "
            >
              <span class="fa fa-pen"></span>
            </div>
          </td>

          <td>
            <div
              @click="deleteTask(index)"
              class="
                text-center text-light
                todo-btn
                border border-danger
                rounded-3
                px-3
                py-1
                page-delete-container
              "
            >
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "TodoApp",
  props: {
    msg: String,
  },

  data() {
    return {
      task: "",
      editedTask: null,
      availableStatuses: ["to-do", "in-progress", "finished"],
      tasks: [
        {
          name: "To do task number one",
          status: "To-Do",
        },
        {
          name: "To do task number two",
          status: "in-progress",
        },
      ],
    };
  },
  methods: {
    submitTask() {
      if (this.task.length === 0) return;


      if (this.editedTask === null) {
        this.tasks.push({
          name: this.task,
          status: "to-do",
        });
      } else {
        this.tasks[this.editedTask].name = this.task; 
        this.editedTask = null; 
      }

      // Set to empty string at end
      this.task = "";
  
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
      console.log(`Task:: ${this.task} has been deleted!`);
    },
    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
    changeStatus(index){
    let newIndex = this.availableStatuses.indexOf(this.tasks[index].status);
    if(++newIndex > 2) newIndex = 0;
    this.tasks[index].status = this.availableStatuses[newIndex];
    },
    firstCharUpper(str){
      return str.charAt(0).toUpperCase() + str.slice(1); 
    }
  },
};
</script>

<style scoped>
html {
  padding: 0;
  margin: 0;
}
.push {
  height: 500px;
  border: 2px solid #fff;
  background: #0000001e;
}
*,
td {
  color: #fff !important;
}
.btn {
  height: 100%;
}
.page-custom-heading {
  padding: 3rem;
  background: #0000001e;
  text-align: center;
}
div.todo-btn:hover {
  background: #7777773a;
}
span.fa:hover {
  background: #ffffff;
}
</style>