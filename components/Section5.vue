<template>
  <div class="section5-container">
    <div class="card">
      <div class="overlay">
        <div class="text-akad">Akad Nikah</div>
        <div class="text-akad-jam">
          <p>
            <strong>Selasa, 01 Februari 2022</strong><br />
            09.00 WIB - 09.30 WIB
          </p>
        </div>
        <div class="text-akad-tempat">
          <p>
            <strong>Kediaman Mempelai Perempuan</strong><br />
            Ds. Baledono, Kec. Purworejo Kab. Purworejo <br />
            Jawa Tengah
          </p>
        </div>
        <div class="divider"></div>
        <div class="text-akad">Resepsi</div>
        <div class="text-akad-jam">
          <p>
            <strong>Selasa, 01 Februari 2022</strong><br />
            09.30 WIB - Selesai
          </p>
        </div>
        <div class="text-akad-tempat">
          <p>
            <strong>Kediaman Mempelai Perempuan</strong><br />
            Ds. Baledono, Kec. Purworejo Kab. Purworejo <br />
            Jawa Tengah
          </p>
        </div>



        <div style="flex-grow: 1"></div>

        <!-- <div class="text-akad-tempat">Counting Down To The Big Day</div> -->

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

        <div class="open-invitation-button" @click="openMap()" data-aos="flip-right" data-aos-duration="2000">
          <br>
        <div class="text-map">KLIK LIHAT LOKASI</div>
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

methods: {
    openMap: function () {
      window.open(
        "https://goo.gl/maps/iKsvPLhbLX5HDjLJ6"
      );
    },
  },

  created() {
    setInterval(() => {
      let distance =
        new Date("1 Feb 2022 09:00:00").getTime() - new Date().getTime();
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
.section5-container {
  display: flex;
  justify-content: center;
  height: 700px;
}

.card {
  overflow: hidden;
  border-radius: 1rem;
  margin: 20px 20px 50px 20px;
  width: 95%;
  /* background-image: url("https://1.bp.blogspot.com/-VQWJuCYB9Rs/X4HIx0_CzzI/AAAAAAAAGuk/C5jNNLVq-IIoUaS1feJGXNaEExg-hkQBACLcBGAsYHQ/s16000/BGJ_0351.jpg") !important; */
  background-image: url("~/assets/images/nia/IJ0_1530.jpg") !important;
  background-size: cover;
  background-position: top center;
}

.text-akad {
  color: burlywood;
  font-size: 30px;
  font-family: "Canvas", sans-serif;
  font-weight: bold;
}

.text-map {
  color: white;
  font-size: 30px;
  font-family: "Canvas", sans-serif;
  font-weight: bold;
}

.text-akad-jam {
  margin-top: 20px;
  color: white;
  /* line-height: 20px; */
}

.text-akad-tempat {
  margin-top: 20px;
  color: white;
  line-height: 20px;
}

.overlay {
  display: flex;
  flex-direction: column;
  padding: 20px;
  padding: 50px 30px 50px 30px;
  text-align: center;
  /* background: rgba(0, 0, 0, 0.6); */
  background: rgb(2, 0, 36);
  background: linear-gradient(
    0deg,
    rgb(0, 0, 0) 0%,
    rgba(255, 255, 255, 0) 100%
  );
  overflow: hidden;
  height: 100%;
  z-index: 2;
}

.divider {
  height: 20px;
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
  color: burlywood;
  display: flex;
  justify-content: center;
}
</style>
