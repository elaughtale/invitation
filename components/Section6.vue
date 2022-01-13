<template>
  <div class="section6-container">
    <div>Counting Down To The Big Day</div>
    <div class="count-down">
      <div class="row">
        <div class="column">
          <div class="time-number">{{ dayCount }}</div>
          <div>Day</div>
        </div>
        <div class="column">
          <div class="time-number">:</div>
        </div>
        <div class="column">
          <div class="time-number">{{ hourCount }}</div>
          <div>Hour</div>
        </div>
        <div class="column">
          <div class="time-number">:</div>
        </div>
        <div class="column">
          <div class="time-number">{{ minuteCount }}</div>
          <div>Min</div>
        </div>
        <div class="column">
          <div class="time-number">:</div>
        </div>
        <div class="column">
          <div class="time-number">{{ secondCount }}</div>
          <div>Sec</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  data() {
    return {
      dayCount: "",
      hourCount: "",
      minuteCount: "",
      secondCount: "",
    };
  },

  created() {
    setInterval(() => {
      let distance =
        new Date("01 Feb 2022 09:00:00").getTime() - new Date().getTime();
      if (distance > 0) {
        // DAY
        if (
          Math.floor(distance / (1000 * 60 * 60 * 24)).toString().length < 2
        ) {
          this.dayCount = `0${Math.floor(distance / (1000 * 60 * 60 * 24))}`;
        } else {
          this.dayCount = Math.floor(
            distance / (1000 * 60 * 60 * 24)
          ).toString();
        }
        // HOUR
        if (
          Math.floor(
            (distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
          ).toString().length < 2
        ) {
          this.hourCount = `0${Math.floor(
            (distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
          )}`;
        } else {
          this.hourCount = Math.floor(
            (distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
          ).toString();
        }
        // MINUTE
        if (
          Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60)).toString()
            .length < 2
        ) {
          this.minuteCount = `0${Math.floor(
            (distance % (1000 * 60 * 60)) / (1000 * 60)
          )}`;
        } else {
          this.minuteCount = Math.floor(
            (distance % (1000 * 60 * 60)) / (1000 * 60)
          ).toString();
        }
        // SECOND
        if (Math.floor((distance % (1000 * 60)) / 1000).toString().length < 2) {
          this.secondCount = `0${Math.floor((distance % (1000 * 60)) / 1000)}`;
        } else {
          this.secondCount = Math.floor(
            (distance % (1000 * 60)) / 1000
          ).toString();
        }
      }
    }, 1000);
  },
});
</script>

<style scoped>
.section6-container {
  display: flex;
  flex-direction: column;
  text-align: center;
}

.time-number {
  font-size: 30px;
  font-weight: bold;
}

.column {
  float: left;
  padding: 5px;
  line-height: 1.5;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  /* display: table; */
  /* clear: both; */
}

.count-down {
  display: flex;
  justify-content: center;
}
</style>
