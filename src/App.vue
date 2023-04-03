<template>
  <div>
    <header>
      <div class="title">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button type="button" @click="handleClick('title')">
          Order by title
        </button>
        <button type="button" @click="handleClick('salary')">
          Order by salary
        </button>
        <button type="button" @click="handleClick('location')">
          Order by location
        </button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Job from "./types/Job";
import OrderByTerm from "./types/OrderByTerm";
import JobList from "./components/JobList.vue";

const jobs = ref<Job[]>([
  { title: "farm worker", location: "lon lon ranch", salary: 30000, id: "1" },
  { title: "quarryman", location: "death mountain", salary: 40000, id: "2" },
  { title: "flute player", location: "the lost woods", salary: 35000, id: "3" },
  { title: "fisherman", location: "lake hylia", salary: 21000, id: "4" },
  { title: "prison guard", location: "gerudo valley", salary: 32000, id: "5" },
]);

const order = ref<OrderByTerm>("title");

// functions
const handleClick = (term: OrderByTerm) => {
  order.value = term;
};
</script>

<style scoped>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
