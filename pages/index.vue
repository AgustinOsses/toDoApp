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
          <input v-model="item.check" type="checkbox" />
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
      if (this.task !== '') {
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
  background: #bdc3c7; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to bottom,
    #2c3e50,
    #bdc3c7
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to bottom,
    #2c3e50,
    #bdc3c7
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  background-repeat: no-repeat;
  /* background-image: url('../assets/images/trigo.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
  background-attachment: fixed; */
}
.lala::placeholder {
  width: 50px;
}
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 2rem 0;
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
  background: rgba(0, 0, 0, 0.5);
  color: #fff;
  padding-left: 1rem;
  outline: none;
}
.input::placeholder {
  color: rgba(255, 255, 255, 0.5);
}

.task-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  /* flex-wrap: wrap; */
  width: 80vw;
  height: 5rem;
  color: #000;
  background-color: rgba(255, 255, 255, 0.9);
  margin: 0.1rem;
  height: 4rem;
  border-radius: 5px;
  padding: 0 0.5rem;
}

.ckeck-task {
  display: flex;
  align-items: center;
}

.delete {
  width: 25px;
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

@media screen and (min-width: 1025px) {
  .input {
    width: 40vw;
    height: 3rem;
  }

  .task-wrapper {
    width: 40vw;
    height: 3rem;
  }
}
</style>
