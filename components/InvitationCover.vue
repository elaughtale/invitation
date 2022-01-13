<template>
  <div class="header-container" id="header-container-id">
    <div class="header-text-component">
      <p>Dear</p>
      <br />
      <p class="guess-name">Yunita Widiyani</p>
      <br />
      <p>You are invited to the wedding of</p>
      <h1 class="brides-name">Taufiq & Yunita</h1>
      <div class="open-invitation-button" @click="toggle()">
        <p>Open Invitation</p>
      </div>
      <!-- <div>
          <vs-button danger border :active="true" @click.native="toggle()">
            <i class="bx bxs-heart"></i> Open Invitation
          </vs-button>
        </div> -->
    </div>
  </div>
</template>

<script>

let audio = require("~/assets/audio/aa.mp3").default;

export default {
  mounted() {
    document.body.classList.add("no-scroll");
  },
  methods: {
    toggle() {
      document
        .getElementById("header-container-id")
        .classList.toggle("m-fadeOut");

      this.audio = new Audio(audio);
      this.audio.play();

      document.body.classList.remove("no-scroll");
    },
  },
};

</script>

<style scoped>
.header-text-component {
  text-align: center;
  color: white;
  margin-top: 50px;
}

.brides-name {
  margin-top: 5%;
  font-family: "Kensington", sans-serif;
  font-size: 86px;
  font-weight: normal;
}

.guess-name {
  font-weight: bold;
  font-size: 24px;
}

.text-content-1 {
  margin-top: 20%;
  font-family: "Kensington Extra", sans-serif;
  font-size: 22px;
}

/* url("https://1.bp.blogspot.com/-VQWJuCYB9Rs/X4HIx0_CzzI/AAAAAAAAGuk/C5jNNLVq-IIoUaS1feJGXNaEExg-hkQBACLcBGAsYHQ/s16000/BGJ_0351.jpg") */

.header-container {
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
  text-align: center;

  width: 100%;
  height: 100%;
  position: fixed;
  background-image: linear-gradient(
      rgba(0, 3, 8, 0.36) 68%,
      rgb(4, 11, 12) 100%
    ),
    url("~/assets/images/nia/TWNT0069.jpg") !important;
  background-size: cover;
  background-position: bottom center;
}

.open-invitation-button {
  position: absolute;
  bottom: 50px;
  left: 50%;
  transform: translateX(-50%);
  /* margin-top: 50px; */
  border-radius: 30px;
  display: inline-block;
  padding: 8px 30px;
  font-family: "Canvas", sans-serif;
  background: rgba(110, 64, 0, 0.7);
  font-weight: bold;
}

.m-fadeOut {
  visibility: hidden;
  opacity: 0;
  transition: visibility 0s linear 1000ms, opacity 1000ms;
}
</style>
