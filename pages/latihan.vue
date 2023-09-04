<template>
  <div class="hello">
<h1>{{ totalMarks }}</h1>
</div>
</template>

<script>
export default {
data() {
return {
number: 3
}
},
computed: {
totalMarks() {
return this.number * 2;
}
}
};
</script>


