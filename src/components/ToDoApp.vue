<template>
  <div>
    <h2 class="title">My To Do Table</h2>

    <!-- ToDoInput -->
    <div class="input-group input-item mb-3">
      <input
        @keyup.enter="submit"
        v-model="task"
        placeholder="Enter your work..."
        type="text"
        class="form-control work-input"
        aria-label="Text input with checkbox Recipient's username"
        aria-describedby="basic-addon2"
      />
      <span
        @click="submit"
        class="input-group-text bg-primary text-white"
        id="basic-addon2"
      >
        <i class="fas fa-plus"></i>
      </span>
    </div>

    <!-- ToDoList -->
    <transition-group name="list" tag="div">
      <div v-for="(task, index) in tasks" :key="index">
        <div class="input-group input-item">
          <div class="input-group-text">
            <input
              class="form-check-input"
              type="checkbox"
              v-model="task.checked"
              value=""
              aria-label="Checkbox for following text input"
            />
          </div>
          <input
            v-model="task.name"
            type="text"
            class="form-control"
            aria-label="Text input with checkbox Recipient's username"
            aria-describedby="basic-addon2"
          />
          <span
            @click="deleteTask(index)"
            class="input-group-text bg-danger text-white"
            id="basic-addon2"
          >
            <i class="fas fa-trash-alt"></i>
          </span>
        </div>
      </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  name: "ToDoApp",
  props: {
    msg: String,
  },
  data() {
    return {
      task: "",
      tasks: [
        {
          id: 0,
          name: "Yangi darsni o'zlashtirish",
          checked: false,
        },
        {
          id: 1,
          name: "Photoshop dasturini o'rganish",
          checked: true,
        },
        {
          id: 2,
          name: "Reactni o'rganish",
          checked: false,
        },
      ],
    };
  },
  methods: {
    submit() {
      if (this.task.trim() == 0) {
        return;
      }

      this.tasks.push({
        name: this.task.trim(),
      });

      this.task = "";
    },
    // updateTask() {
    //   console.log(this.task.name);
    // },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.title {
  margin: 20px 0;
  font-weight: 600;
}
.input-item {
  margin: 20px 0;
}
label {
  display: block;
  width: 100%;
}
input {
  width: 90%;
  margin: 5px;
  font-size: 1.05rem;
  border-color: #ccc;
  border-radius: 8px;
  padding: 7px;
}
input:focus {
  border-color: #ccc;
  outline: none;
}
.input-group:not(.has-validation) > .dropdown-toggle:nth-last-child(n + 3),
.input-group:not(.has-validation)
  > :not(:last-child):not(.dropdown-toggle):not(.dropdown-menu),
.input-group-text {
  border-top-right-radius: 0;
  border-bottom-right-radius: 0;
  height: 2.6rem;
  margin-top: 0.311rem;
  border-radius: 0.7rem 0 0 0.7rem;
}
.input-group {
  width: 90%;
  margin: auto;
}
#basic-addon2 {
  margin-left: -0.5rem;
  border-radius: 0 0.7rem 0.7rem 0;
  cursor: pointer;
}
.form-check-input,
.form-check-input:checked {
  box-shadow: none;
  margin: 0px;
  cursor: pointer;
}
.form-control:active {
  outline: none;
  box-shadow: none;
}
textarea:focus,
textarea.form-control:focus,
input.form-control:focus,
input[type="text"]:focus,
input[type="password"]:focus,
input[type="email"]:focus,
input[type="number"]:focus,
[type="text"].form-control:focus,
[type="password"].form-control:focus,
[type="email"].form-control:focus,
[type="tel"].form-control:focus,
[contenteditable].form-control:focus {
  box-shadow: inset 0 -1px 0 #ddd;
}
.work-input {
  padding-left: 1.5rem;
}

.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active,
.list-leave-active {
  transition: all 1s ease;
}
.list-enter, 
.list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(50px);
}
</style>
