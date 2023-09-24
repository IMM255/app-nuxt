<template>
  <div class="container">
    <div v-for="task in tasks" :key="task.id">
      <div
          v-if="task.id == paramId"
          class="item-task d-flex align-items-start pt-3 pb-4"
          >
          <input
            id="task"
            v-model="task.isDone"
            type="checkbox"
            name="status"
            class="me-2 mt-2"
            :checked="task.isDone"
            >
          <div>
            <div class="title-task mb-1">
              {{task.title}}
            </div>
            <div class="description-task small text-muted mb-3" type="date">
              {{task.description}}
            </div>
            <input type="date" class="form-control form-control-sm">
          </div>
      </div>
    </div>

    <div class="action mt-4">
      <div class="btn btn-outline-secondary btn-sm mb-3" @click="$router.go(-1)">
        Kembali
      </div>
    </div>
  </div>


</template>

<script>
export default {
  layout (context){
    return 'custom'
  },
      data(){
        return{
          paramId: this.$route.params.id,
          tasks: [
{
id: 1,
title: 'Task 1',
description: 'ini makanan terenak',
isDone: false,
},
{
id: 2,
title: 'Task 2',
description: 'ini resep makanan terbaru 2',
isDone: false,
},
{
id: 3,
title: 'Task 3',
description: ' ini makanan terlaris',
isDone: false,
}
],
        }
      }
}
</script>

<style>

</style>
