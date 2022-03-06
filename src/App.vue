<template>
  <div class="page">
    <Basket v-bind="state" />

    <div class="form">
      <div>H/W Ratio: {{ (state.height / state.width).toFixed(2) }}</div>

      <div class="input">
        <div>Width</div>
        <input type="number" v-model="state.width" />
      </div>
      <div class="input">
        <div>Height</div>
        <input type="number" v-model="state.height" />
      </div>
      <div class="input">
        <div>Gap</div>
        <input type="number" v-model="state.gap" />
      </div>
      <div class="input">
        <div>Rows</div>
        <input type="number" v-model="state.rows" />
      </div>
      <div class="input">
        <div>Columns</div>
        <input type="number" v-model="state.columns" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from "vue";
import Basket from "./Basket.vue";

const state = reactive({
  width: 25,
  height: 50,
  rows: 2,
  columns: 2,
  gap: 5,
});
</script>

<style scoped>
.page {
  padding: 50px;
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  height: 100%;
}

.form {
  display: flex;
  gap: 5px;
  flex-direction: column;
  margin-top: 20px;
}

.input {
  display: flex;
  flex-direction: row;
  gap: 10px;
  align-items: center;
}

.input div {
  width: auto;
  min-width: 60px;
}
</style>
