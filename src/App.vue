<script setup>
import { ref, watch } from "vue";
import q from "./assets/Data/quiz.json";
import Card from "./assets/Components/Card.vue"



const quizes = ref(q);
const search = ref("");

watch(search, () => {
  quizes.value = q.filter((quiz) =>
    quiz.name.toLocaleLowerCase().includes(search.value.toLocaleLowerCase())
  );
});
</script>

<template>
  <div class="container">
    <header>
      <h1>quizes</h1>
      <input
        type="text"
        name=""
        id=""
        placeholder="search....."
        v-model.trim="search"
      />
    </header>

    <div class="options-container">
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz"/>
      <!-- <div v-for="quiz in quizes" :key="quiz.id" class="card">
        <img :src="quiz.img" alt="" />
        <div class="card-text">
          <h2>{{ quiz.name }}</h2>
          <p>{{ quiz.questions.length }} Question</p>
        </div>
      </div> -->
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
}
header {
  margin: 30px 0 10px;
  display: flex;
  align-items: center;
}
header h1 {
  font-weight: bold;
  margin-right: 30px;
}
header input {
  border: none;
  background-color: rgb(211, 198, 198);
  padding: 10px;
  border-radius: 5px;
}

/* card */

.card {
  width: 310px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  margin: 20px 10px 35px;
  cursor: pointer;
}
.card img {
  width: 100%;
  height: 190px;
  margin: 0;
}
.card .card-text {
  padding: 0 5px;
}
.card .card-text h2 {
  font-weight: bold;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}
</style>
