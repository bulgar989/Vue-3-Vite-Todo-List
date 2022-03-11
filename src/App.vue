<template>
  <div class="header">
    <div class="container">
      <div class="logo">ToDo List</div>
      <div class="form">
        <input type="text">
        <button class="btn">Add a new task</button>
      </div>
    </div>
  </div>
  <div class="container">
    <h2>
      <span>To Do</span>
      <span class="mask-num">10</span>
    </h2>
    <ul class="mask-list">
      <li>
          <div>
            <input type="checkbox">
            <span>New video</span>
          </div>
        <button class="btn-remove">Remove</button>
      </li>
    </ul>
    <h2>
      <span>Done</span>
      <span class="mask-num">10</span>
    </h2>
    <ul class="mask-list">
      <li>
        <div>
          <input type="checkbox">
          <span>Add code</span>
        </div>
        <button class="btn-remove">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
def
</script>
