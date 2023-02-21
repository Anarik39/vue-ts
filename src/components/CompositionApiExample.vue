<template>
  <div class="job-list">
    <div>
      <!--  Выдаст ошибку, т.к. тип не совпадает с OrderTerm  -->
      <!--      <button @click="handleClick('test')">test</button>  -->
      <button @click="handleClick('title')">title</button>
      <button @click="handleClick('location')">location</button>
      <button @click="handleClick('salary')">salary</button>
    </div>

    <div>sort by {{ order }}</div>

    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>

        <div class="salary">
          <p>{{ job.salary }} rupees</p>
        </div>

        <div class="description">
          <p>Lorem ipsum dolor sit</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts" setup>
import type Job from "@/types/Job";
import type OrderTerm from "@/types/OrderTerm";
import { computed, ref, toRefs } from "vue";

interface Props {
  jobs?: Job[]; // делаем не обяз проп
}

/* const props = defineProps<Props>(); */ // без объявления дефолтных значений

const props = withDefaults(defineProps<Props>(), {
  jobs: () => [],
});

const order = ref<OrderTerm>("title");
const { jobs } = toRefs(props);

const handleClick = (term: OrderTerm) => {
  order.value = term;
};

const orderedJobs = computed(() => {
  return [...jobs.value].sort((a: Job, b: Job) => {
    return a[order.value] > b[order.value] ? 1 : -1;
  });
});
</script>

<style scoped>
.job-list {
  border-right: 1px solid white;
  padding-right: 50px;
}

.job-list ul {
  padding: 0;
}

.job-list li {
  list-style-type: none;
  background: #732b2b;
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
  font-weight: bold;
  margin: 10px 4px;
}
</style>
