<!-- eslint-disable vue/require-valid-default-prop -->
<!-- eslint-disable vue/require-valid-default-prop -->
<!-- eslint-disable vue/no-mutating-props -->
<!-- eslint-disable vue/require-default-prop -->
<template>
  <div
        :class="['item-task d-flex align-items-center border-bottom pt-3 pb-4',
              isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12']">
          <input
          v-if="task.hasOwnProperty('isDone')"
          id="task"
          v-model="task.isDone"
          type="checkbox"
          name="status"
          class="me-2"
          :checked="task.isDone">
          <div
          :class="['d-flex flex-column', task.isDone ?
          'text-decoration-line-through fst-italic': '' ]"
          >
              <nuxt-link class="title-task mb1" :to="path +'/'+ task.id">{{ task.title}}</nuxt-link>
              <div class="description-task small text-muted">{{ task.description}}</div>
              <div v-if="task.hasOwnProperty('img')"
>
                <img :src="task.img" style="width:300px">
              </div>
              <input
v-if="task.hasOwnProperty('isDone')"
class="form-control form-control-sm" type="date" >
          </div>
        </div>
</template>

<script>
export default {
    // eslint-disable-next-line vue/require-default-prop
    props: {
      task: {
        type: Object,
        default(){
          return {}
        }
      },
      path: {
        type: String,
        default(){
        }
      },
      isGrid: {
        type: Boolean,
        required: true,
        default: false
      }
    },
    computed: {
      localTask: {
        get(){
          return this.task
        },
        set (newValue){
          this.$emit('update:task', newValue)
        }
      }
    }
  }
</script>


