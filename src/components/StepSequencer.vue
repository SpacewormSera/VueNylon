<template>
  <div class="container">
    <SequencerController     
      v-on:run-sequence="runSequence"
    />
    <div class="container">
      <SequencerItem 
      v-for="(step, i) of steps" 
      v-bind:step="step" 
      v-bind:index="i"
      />
    
    </div>
  </div>
</template>

<script>
import SequencerItem from "@/components/SequencerItem";
import SequencerController from "@/components/SequencerController";
export default {
  props: ["steps"], 
  components: {
    SequencerItem,
    SequencerController,
  },
  methods: {
    runSequence(step){
      this.$emit('run-sequence', step)
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  border: 1px solid rgb(163, 163, 163);
}
</style>