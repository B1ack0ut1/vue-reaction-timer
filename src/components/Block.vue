<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
      startTime: 0,
      stopTime: 0,
    };
  },
  mounted() {
    console.log("component mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  updated() {
    console.log("component updated");
  },
  unmounted() {
    console.log("component unmounted");
  },
  methods: {
    startTimer() {
      this.startTime = Date.now();
    },
    stopTimer() {
      this.endTime = Date.now();
      this.reactionTime = this.endTime - this.startTime;
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
