<template>
  <q-page class="bg-grey-3 column">
    <div class="row q-pa-sn bg-primary">
      <q-input
      v-model="newTask"
      @keyup.enter="addTask"
      filled 
      class="col" square
      bg-color="white"  placeholder="Add task" dense>
    
        <template v-slot:append>
          <q-btn 
          @click="addTask"
          round dense flat icon="add" />
        </template>
      </q-input>
    </div>

    <q-list class="bg-white"
    separator
    bordered>
 
      <q-item 
      v-for="(task, index) in task"
      :key="task.title"
      @click="task.done = !task.done"
      :class="{ 'done bg-blue-1' : task.done}"
      clickable
      v-ripple>
        <q-item-section avatar>
          <q-checkbox
           v-model="task.done" 
           class="no-pointer-events"
           color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
      </q-item>

      <q-item-section
      v-if="task.done"
      >
      <q-btn 
      @click.stop="deleteTask(index)"
      flat round dense color="primary" icon="delete" />
        </q-item-section>
      

    </q-list>
    
  </q-page>
</template>

<script>
import { TouchSwipe } from 'quasar'
import { defineComponent } from 'vue'

export default {
  data() {
    return {
      newTask : '',
      tasks: {
        title: 'Get banana',
        done: false
      },
      
        title: 'Eat banana',
        done: true
    },
    {
        title: 'Throw banana',
        done: false
  }
},
methods: {
  deleteTask(index) {
    this.$q.dialog({
        title: 'Confirm',
        message: 'Really delete?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.task.splice; {index, 1}
        this.$q.notify('Task deleted')
 
    },
    addTask(), {
      this:task.push({
        title: this.newTask,
        done:false
      }),
      this:newTask= ''
    }
  

</script>

<style lang="scss">

  .done {
    .q-item__label {
      text-decoration: line-through;
      color: #bbb;
    }
  }
</style>