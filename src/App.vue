<template>
  <div class="header">
    <div class="container">
      <div class="logo">ToDo List</div>
      <div class="form">
        <input type="text" :value = "valueInput" @input="handyInput" @keypress.enter="addTask">
        <button class="btn" @click="addTask">Add a new task</button>
      </div>
    </div>
  </div>
  <div class="container">
    <h2>
      <span>To Do</span>
      <span class="mask-num">{{ needDoList.length }}</span>
    </h2>
    <ul class="mask-list">
      <li v-for="(mask, index) in needDoList" :key="mask.id">
          <div>
            <input type="checkbox" @change="doCheck(index, 'need')">
            <span>{{ mask.title }}</span>
          </div>
        <button class="btn-remove" @click="removeMask(index, 'need')">Remove</button>
      </li>
    </ul>
    <h2>
      <span>Done</span>
      <span class="mask-num">{{ completeList.length }}</span>
    </h2>
    <ul class="mask-list complete-list">
      <li v-for="(mask, index) in completeList" :key="mask.id">
        <div>
          <input type="checkbox" @change="doCheck(index, 'complete')" checked>
          <span>{{ mask.title }}</span>
        </div>
        <button class="btn-remove" @click="removeMask(index, 'complete')">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return {
      valueInput: '',
      needDoList: [
        {id: 1, title: 'Мука'},
        {id: 2, title: 'Молоко'},
        {id: 3, title: 'Мука'},
        {id: 4, title: 'Пшено'}
      ],
      completeList: [
        {id: 1, title: 'Гречка'},
        {id: 2, title: 'Тушнка'},
        {id: 3, title: 'Забраться на гору'},
        {id: 4, title: 'Мука'},
        {id: 5, title: 'Посадить дерево'}
      ]
    }
  },
  methods: {
    handyInput (event) {
      this.valueInput = event.target.value
    },
    addTask() {
      if(this.valueInput === '') { return }
      this.needDoList.push({
        title: this.valueInput,
        id: Math.random()
      })
      this.valueInput = ''
    },
    doCheck (index, type) {
      if (type === 'need') {
        const completeMask = this.needDoList.splice(index, 1)
        this.completeList.push(...completeMask)
      }else{
        const noCompleteMask = this.completeList.splice(index, 1)
        this.needDoList.push(...noCompleteMask)
      }
    },
    removeMask (index, type) {
      const ToDoList = type === 'need' ? this.needDoList : this.completeList
      ToDoList.splice(index, 1)
    }
  }
}


</script>

