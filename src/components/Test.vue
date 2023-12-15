<script setup>
import "../block.css";
import { ref, reactive, resolveDirective } from "vue";
import { inject } from "vue";
import { provide } from "vue";
import Color from "./Color.vue";

const classBlock = ref("block-list");
const check = ref(false);
const props = defineProps(["title", "blue", "red", "yellow", "green"]);

let classHandler = () => {
  if (classBlock.value === "block-list") {
    classBlock.value = classBlock.value + " " + "active";
  } else {
    classBlock.value = "block-list";
  }
};

const checkBlock = ref("block-check");

let viewHandler = () => {
  if (checkBlock.value == "block-check") {
    checkBlock.value = checkBlock.value + " " + "active";
    check.value = true;
  } else {
    checkBlock.value = "block-check";

    check.value = false;
  }
};

const items = ref([
  {
    number: 1,
    value: props.red,
    color: "color-box red",
    check: false,
  },
  {
    number: 2,
    value: props.yellow,
    color: "color-box yellow",
    check: false,
  },
  {
    number: 3,
    value: props.green,
    color: "color-box green",
    check: false,
  },
  {
    number: 4,
    value: props.blue,
    color: "color-box blue",
    check: false,
  },
]);

let updateValue = (event, item) => {
  console.log(event.value, this);
  item.value = event.value;
};

provide("items", items);
provide("title", props.title);
</script>

<template>
  <div class="classBlock">
    <div class="block-lists-all">
      <div :class="classBlock">
        <div>
          <div class="arrow" @click="classHandler"></div>
          <div :class="checkBlock" @click="viewHandler"></div>
          <div class="title">
            <p>{{ props.title }}</p>
          </div>
        </div>
        <div>
          <ul class="list">
            <li v-for="item in items">
              <div>
                <input
                  :checked="item.check"
                  type="checkbox"
                  @input="item.check = Number($event.target.checked)"
                />
                <p>Item {{ item.number }}</p>
              </div>
              <div>
                <input
                  type="number"
                  :value="item.value"
                  @input="item.value = Number($event.target.value)"
                />
                <div :class="item.color"></div>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="color-block-all">
      <Color v-if="check" />
    </div>
  </div>
</template>
