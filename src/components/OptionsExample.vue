<template>
  <div class="options-api">
    <p>{{ name }} - {{ age }}</p>
    <button @click="changeName('Zelda')">change name</button>
    <button @click="changeAge('30')">change age</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import type { StringWithNumber } from "@/types/Options";

export default defineComponent({
  name: "OptionsExample",

  data() {
    return {
      name: "Link",
      age: 25 as StringWithNumber,
    };
  },

  methods: {
    changeName(name: string): string {
      this.name = name;

      return name;
    },

    changeAge(age: StringWithNumber) {
      this.age = age;
    },
  },
});
</script>

<style>
.options-api {
  text-align: right;
}
</style>
