<template>
  <div class="container">
    <h1 class="title">{{ title }}</h1>
    <input
      v-model="task"
      @keyup.enter="add"
      class="input"
      type="text"
      maxlength="20"
      placeholder="Add a Task"
    />

    <div v-for="(item, index) in tasklist" :key="index">
      <div class="task-wrapper">
        <div class="ckeck-task">
          <input v-model.trim="item.check" type="checkbox" />
          <p class="task" :class="{ done: item.check }">
            {{ item.name }}
          </p>
        </div>

        <button @click="remove(index)">
          <img class="delete" src="@/assets/images/trash.svg" alt="" />
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasklist: [],
      title: 'TODO-LIST',
      task: '',
    }
  },

  methods: {
    add() {
      if (this.task.trim().length > 0) {
        this.tasklist.push({ name: this.task, check: false })
        this.task = ''
      }
    },

    remove(index) {
      // const index = this.tasklist.indexOf(task)
      this.tasklist.splice(index, 1)
    },
  },
}
</script>

<style lang="css">
body {
  height: 100vh;
  background-color: #e0e5ec;
}
.lala::placeholder {
  width: 50px;
}
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 2rem 0;
}

.title {
  color: #000;
}

.input {
  width: 80vw;
  height: 4rem;
  font-size: 20px;
  border-radius: 5px;
  border: none;
  margin: 1rem 2rem;
  background: #e0e5ec;
  box-shadow: inset 5px 5px 10px #b8bcc2, inset -5px -5px 10px #ffffff;
  padding-left: 1rem;
  outline: none;
}
.input::placeholder {
  color: gray;
}

.task-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 80vw;
  height: 3.5rem;
  color: #000;
  border-radius: 5px;
  background: #e0e5ec;
  background: linear-gradient(145deg, #caced4, #f0f5fd);
  box-shadow: 5px 5px 10px #b8bcc2, -5px -5px 10px #ffffff;
  margin: 0.4rem;
  padding: 0 0.5rem;
}

.ckeck-task {
  display: flex;
  align-items: center;
}

.delete {
  width: 40px;
  border-radius: 5px;
  background: #e0e5ec;
  box-shadow: 5px 5px 10px #b8bcc2, -5px -5px 10px #ffffff;
  padding: 0.4rem;
}

.task {
  display: flex;
  flex-wrap: wrap;
  font-size: 20px;
  padding-left: 0.5rem;
  width: 70;
}

.done {
  text-decoration: line-through;
}

input[type='checkbox'] {
  transform: scale(2);
  margin: 0 0.5rem;
  outline: none;
}

button {
  border: none;
  outline: none;
  background: transparent;
}

.bgGray {
  background-color: #dddddd;
}

@media screen and (min-width: 1025px) {
  .input {
    width: 40vw;
    height: 3rem;
  }

  .task-wrapper {
    width: 40vw;
  }
}
</style>
