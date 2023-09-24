<template>
  <div class="container">
    <div v-for="article in articles" :key="article.id">
      <div
          v-if="article.id == paramId"
          class="item-task d-flex align-items-start pt-3 pb-4"
          >
          <div>
            <img :src="article.img" style="width:400px" alt="">
          </div>
          <div>
            <div class="title-task mb-1 ms-3">
              {{article.title}}
            </div>
            <div class="description-task small text-muted mb-3 ms-3" type="date">
              {{article.description}}
            </div>
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
      data(){
        return{
          paramId: this.$route.params.id,
         articles: [
	{
    id:1,
    title:"Judul Artikel 1",
    description :"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Placeat dolor explicabo sint quos exercitationem fugiat reiciendis assumenda. Ad quia veritatis, dolor odit, voluptas numquam modi porro eius reprehenderit ullam tenetur?",
		img: 'https://images.unsplash.com/photo-1649282806617-c51bb282899c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80'
  },
	{
    id:2,
    title:"Judul Artikel 2",
    description :"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Placeat dolor explicabo sint quos exercitationem fugiat reiciendis assumenda. Ad quia veritatis, dolor odit, voluptas numquam modi porro eius reprehenderit ullam tenetur?",
		img: 'https://images.unsplash.com/photo-1635732646038-0a1a2fe3f2d6?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1074&q=80'
  },
	{
    id:3,
    title:"Judul Artikel 3",
    description :"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Placeat dolor explicabo sint quos exercitationem fugiat reiciendis assumenda. Ad quia veritatis, dolor odit, voluptas numquam modi porro eius reprehenderit ullam tenetur?",
		img: 'https://images.unsplash.com/photo-1640006807976-a6127e9d6fa0?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1171&q=80'
  },
]
        }
      }
}
</script>

<style>

</style>
