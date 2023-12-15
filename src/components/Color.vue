<script setup>
import "../block.css";
import { inject } from "vue";
import { provide } from "vue";
import { ref, reactive } from "vue";

let itms = inject("items");
let title = inject("title");
</script>

<template>
  <div class="classBlock">
    <div class="title">{{ title }}</div>
    <div>
      <ul class="list">
        <li v-for="item in itms">
          <div
            v-if="item.check"
            v-for="n in item.value"
            :class="item.color"
          ></div>
        </li>
      </ul>
    </div>
  </div>
</template>
