<template>
  <composition-api-example :jobs="jobs" />

  <options-example />
</template>

<script lang="ts" setup>
import { reactive, ref } from "vue";
import type Job from "@/types/Job";
import OptionsExample from "@/components/OptionsExample.vue";
import CompositionApiExample from "@/components/CompositionApiExample.vue";

const state = reactive({
  name: "Link",
  age: 25 as number | string,
});

// state.name = 999; // выдаст ошибку, т.к. тип автоматически строка
state.age = "26";

const name = ref("Link"); // автомат тип строка
const age = ref<number | string>(25);

const jobs = ref<Job[]>([
  {
    title: "farm worker",
    location: "lon lon ranch",
    salary: 30000,
    id: "1",
  },
  {
    title: "quarryman",
    location: "death mountain",
    salary: 40000,
    id: "2",
  },
  {
    title: "flute player",
    location: "the lost woods",
    salary: 35000,
    id: "3",
  },
  { title: "fisherman", location: "lake hylia", salary: 21000, id: "4" },
  {
    title: "prison guard",
    location: "gerudo valley",
    salary: 32000,
    id: "5",
  },
]);
</script>
