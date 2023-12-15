<script setup>
import { ref, reactive } from "vue";
import { provide } from "vue";
import { inject } from "vue";
import Test from "./components/Test.vue";
import Color from "./components/Color.vue";
</script>

<template>
  <Test
    v-bind:title="'List 1'"
    v-bind:red="2"
    v-bind:yellow="10"
    v-bind:green="2"
    v-bind:blue="2"
  />
  <Test
    v-bind:title="'List 2'"
    v-bind:red="2"
    v-bind:yellow="2"
    v-bind:green="2"
    v-bind:blue="2"
  />
</template>
