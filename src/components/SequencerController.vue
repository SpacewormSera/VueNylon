<template>
  <div class="seqControl">
    <!-- <button class="seqBtn" v-on:click="runSequence">Play</button> -->
    <button class="seqBtn" v-on:click="$emit('run-sequence')">Play</button>
    <button class="seqBtn" v-on:click="pauseSequence">Pause</button>
    <button class="seqBtn" v-on:click="stopSequence">Stop</button>
    <button class="seqBtn">1</button>
    <button class="seqBtn">2</button>
    <button class="seqBtn">4</button>
    <button class="seqBtn">8</button>
  </div>
</template>

<script>
export default {
  data(){
    return {
      stepAmount: 2
    }
  },
  props: [
    // stepAmount: Number,
    'steps'
  ],
  methods: {
    runSequence() {
      let currentStep = 0;
      setInterval(() => {
        console.log(currentStep += 1);
        if(currentStep >= this.stepAmount){
          currentStep = 0;
        }
      }, 1000);
      // return stepInterval;
    },
    pauseSequence() {
       console.log('pause');
    },
    stopSequence() {
      console.log('stop');
    },
  },
};
</script>

<style scoped>
.seqBtn {
  background-color: #4caf50; /* Green */
  border: none;
  outline: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.seqBtn:hover {
  background-color: rgb(0, 155, 77);
}

.seqBtn:focus {
  background-color: rgb(0, 128, 64);
}

.itemHead {
  border: 1px solid grey;
  width: 100%;
}
</style>