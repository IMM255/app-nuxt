<template>
  <div class="py-4">
    <div class="container">
      <div class="title border-bottom">
        <h5>Task</h5>
        <div class="d-flex align-items-center">
        <span class="me-2">View As</span>
        <button
        class="btn btn-outline-secondary py-1 px-3"
        @click="isGrid = !isGrid"
        >
        {{ isGrid ? 'Grid' : 'List' }}
        </button>
      </div>
      </div>
      <div class="list-task row">
        <div
        :class="['item-task d-flex align-items-center border-bottom pt-3 pb-4',
              isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12']">
          <input
          id="task"
          v-model="task[1].isDone"
          type="checkbox"
          name="status"
          class="me-2"
          :checked="task[1].isDone">
          <div
          :class="['d-flex flex-column', task[1].isDone ?
          'text-decoration-line-through fst-italic': '' ]"
          >
              <div class="title-task mb1">{{ task[1].title}}</div>
              <div class="description-task small text-muted">{{ task[1].description}}</div>
          </div>
        </div>
        <div
        :class="['item-task d-flex align-items-center border-bottom pt-3 pb-4',
              isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12']">
          <input
          id="task"
          v-model="task[2].isDone"
          type="checkbox"
          name="status"
          class="me-2"
          :checked="task[2].isDone">
          <div
          :class="['d-flex flex-column', task[2].isDone ?
          'text-decoration-line-through fst-italic': '' ]"
          >
              <div class="title-task mb1">{{ task[2].title}}</div>
              <div class="description-task small text-muted">{{ task[0].description}}</div>
          </div>
        </div>
        <div
        :class="['item-task d-flex align-items-center border-bottom pt-3 pb-4',
              isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12']">
          <input
          id="task"
          v-model="task[0].isDone"
          type="checkbox"
          name="status"
          class="me-2"
          :checked="task[0].isDone">
          <div
          :class="['d-flex flex-column', task[0].isDone ?
          'text-decoration-line-through fst-italic': '' ]"
          >
              <div class="title-task mb1">{{ task[0].title}}</div>
              <div class="description-task small text-muted">{{ task[0].description}}</div>
          </div>
        </div>
      </div>
      <div class="action py-2">
        <a v-if="!isCreating" href="#" class="add-button" @click="isCreating = !isCreating">Add Task</a>
        <div v-else class="add-card" >
          <div class="card mb-2">
            <div class="card-body d-flex flex-column p-0">
              <input type="text" class="form-control border-0 mb-2" placeholder="Title">
              <textarea id="" class="form-control border-0 small" name="" cols="30" rows="10" placeholder="Description">
              </textarea>
            </div>
          </div>
          <div class="button-wrapper d-flex">
            <button class="btn btn-primary me-2">Save</button>
            <button class="btn btn-outline-secondary" @click="isCreating = !isCreating">Cancel</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    data(){
      return{
        // status sebelum menambhakn task
        isGrid: false,
        isCreating: false,
        // daftar task
        task: [
          {
            title: 'Task 1',
            description: 'Deskripsi Task 1',
            isDone: false,
          },
          {
            title: 'Task 2',
            description: 'ini deskripsi 2',
            isDone: false,
            },
            {
            title: 'Task 3',
            description: ' ini deskripsi 3',
            isDone: false,
            }
        ]
      }
    }
  }

</script>
<style>
</style>
