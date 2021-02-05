<template>
  <div class="seqItem">
    <div v-bind:class="{ itemHeadActive: step.active }" class="itemHead">
      {{ index + 1 }}
    </div>
    <br /><br />
    <div>midi: {{ step.midi }}</div>
    <br />
    <div>osc: {{ step.osc }}</div>
  </div>
</template>

<script>
export default {
  props: {
    step: {
      type: Object,
      required: true,
    },
    index: Number,
  },
};
</script>

<style scoped>
.seqItem {
  display: flex;
  flex-direction: column;
  /* flex-wrap: wrap; */
  flex-grow: 1;
  align-items: flex-start;
  border: 1px solid grey;
  min-width: 400px;
  min-height: 100px;
}

.itemHead {
  border: 1px solid grey;
  width: 100%;
}

.itemHeadActive {
  border: 1px solid grey;
  background: rgb(22, 255, 99);
  width: 100%;
}
</style>