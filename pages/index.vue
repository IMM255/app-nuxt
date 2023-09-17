<template>
  <div class="py-4">
    <div class="container">
      <div class="title border-bottom">
        <h5>Task</h5>
      <div class="d-flex align-items-center">
          <input v-model="searchQuery" type="text" class="form-control" placeholder="Search">
      <div class="d-flex align-items-center justify-content-end w-100">
      <select v-model="searchCategory" class="form-select" aria-label="Default select example">
        <option disabled value="">Pilih category</option>
        <option value="">Semua</option>
        <option >Terbaru</option>
        <option >Terlaris</option>
        <option >Terenak</option>
      </select>
        <span class="me-2">View As</span>
        <button
        class="btn btn-outline-secondary py-1 px-3"
        @click="isGrid = !isGrid"
        >
        {{ isGrid ? 'Grid' : 'List' }}
        </button>
      </div>
      </div>
    </div>
      <!-- <div class="list-task row">
        <CardItem :task="tasks[0]" :isGrid="isGrid" />
        <CardItem :task="tasks[1]" :isGrid="isGrid" />
        <CardItem :task="tasks[2]" :isGrid="isGrid" />
      </div> -->
      <div class="list-task row">
        <CardItem
          v-for="(task, i) in SearchResult"
          :key="i"
          :task="task"
          :is-grid="isGrid"
          />
      </div>
      <form v-on:submit.prevent="appendArray" ref="form">
      <div class="action py-2">
        <a v-if="!isCreating" href="#" class="add-button" @click="isCreating = !isCreating">Add Task</a>
        <div v-else class="add-card" >
          <div class="card mb-2">
            <div class="card-body d-flex flex-column p-0">
              <input v-model="tasks.title" type="text" class="form-control border-1 mb-2" placeholder="Title" required>
              <textarea v-model="tasks.description" class="form-control border-1 small" name="" cols="30" rows="10" placeholder="Description" required>
              </textarea>
              <br>
              <label for="category">Kategori : </label>
              <select v-model="tasks.category" id="category" class="form-select" aria-label="Default select example" required>
                  <option disabled>Pilih category</option>
                  <option>Terbaru</option>
                  <option>Terlaris</option>
                  <option>Terenak</option>
              </select>
            </div>
          </div>
          <div class="button-wrapper d-flex">
            <button class="btn btn-primary me-2">Save</button>
            <button class="btn btn-outline-secondary" @click="isCreating = !isCreating">Cancel</button>
          </div>
        </div>
      </div>
      </form>
    </div>
    <section class="content">
      <br>
      <ul v-if="tasks.name !== ''">
        <li v-for="(item, k) in tasks" :key="k">
          <strong>{{ k }}:</strong> {{ item }}
        </li>
      </ul>
    </section>
  </div>

</template>
<script>
import CardItem from "@/components/Card/CardItem.vue"
  export default {
    components:{
      CardItem
    },
    data(){
      return{
        // variabel penampung teks pencarian
        searchQuery:'',
        searchCategory:'',
        // daftar task
        isGrid: false,
        // status sebelum menambhakn task
        isCreating: false,
        tasks: [
          // {
          //   title: 'Task 1',
          //   description: 'Ini makanan terenak',
          //   isDone: false,
          //   category: 'Terenak',
          // },
          // {
          //   title: 'Task 2',
          //   description: 'ini resep makanan terbaru',
          //   isDone: false,
          //   category: 'Terbaru',
          //   },
          //   {
          //   title: 'Task 3',
          //   description: ' ini makanan terlaris',
          //   isDone: false,
          //   category: 'Terlaris',
          // }
        ],
      }
    },
    computed: {
      SearchResult(){
        if(!this.searchCategory){
          return this.resultQuery(this.tasks)
        }
        if(!this.resultQuery){
          return this.resultCategory(this.tasks)
        }
        return this.resultCategory(this.resultQuery(this.tasks))
    }
    },
    methods: {
       resultQuery(tasks){
        if(this.searchQuery){
          return tasks.filter((item) => {
            return this.searchQuery
            .toLowerCase()
            .split(" ")
            .every((v) => item.title.toLocaleLowerCase().includes(v));
          });
        }else{
          console.log(this.tasks)
          return this.tasks
        }
      },
      resultCategory(tasks){
        if(this.searchCategory){
          return tasks.filter((item) => {
            return this.searchCategory
            .toLowerCase()
            .split(" ")
            .every((v) => item.category.toLocaleLowerCase().includes(v));
          });
        }else{
          console.log(this.tasks)
          return this.tasks
        }
      },
      appendArray(){
        this.tasks.push({
          title:this.tasks.title,
          description:this.tasks.description,
          category:this.tasks.category,
        })
        this.tasks.title = ''
        this.tasks.description = ''
        this.tasks.category = ''
    }
    }
  }

</script>
<style>
</style>
