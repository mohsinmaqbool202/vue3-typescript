<template>
  <div class="job-list">
    <p>Ordered BY : {{ order }}</p>
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptas
            nostrum dicta obcaecati error repudiandae consequatur aliquam
            quaerat eveniet sed unde cupiditate quod optio quibusdam, distinctio
            sapiente, vel ducimus aperiam consequuntur?
          </p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<script setup lang="ts">
import Job from "../types/Job";
import { computed, PropType } from "vue";
import OrderByTerm from "../types/OrderByTerm";

const props = defineProps({
  jobs: {
    type: Array as PropType<Job[]>,
    required: true,
  },
  order: {
    type: String as PropType<OrderByTerm>,
    required: true,
  },
});

//   computed properties
const orderedJobs = computed(() => {
  return [...props.jobs].sort((a: Job, b: Job) => {
    return a[props.order] > b[props.order] ? 1 : -1;
  });
});
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}

/* transition */
.list-move {
  transition: all 1sex;
}
</style>
