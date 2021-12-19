<template>
  <div class="flex flex-col gap-y-4 items-center">
    <h2>{{ dailyPicture.title }}</h2>
    <div class="main">
      <div
        class="d1"
        :style="{ 'background-image': `url(${dailyPicture.url})` }"
      ></div>
      <div
        class="d2"
        :style="{ 'background-image': `url(${dailyPicture.url})` }"
      ></div>
      <div
        class="d3"
        :style="{ 'background-image': `url(${dailyPicture.url})` }"
      ></div>
      <div
        class="d4"
        :style="{ 'background-image': `url(${dailyPicture.url})` }"
      ></div>
    </div>
    <p>{{ dailyPicture.explanation }}</p>
    <div>
      <p>{{ dailyPicture.copyright }}</p>
      <p>{{ dailyPicture.date }}</p>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  data() {
    return {
      dailyPicture: {},
    };
  },
  beforeMount() {
    this.axios
      .get(
        `https://api.nasa.gov/planetary/apod?api_key=${process.env.VUE_APP_API_KEY}`
      )
      .then(response => {
        console.log(response);
        this.dailyPicture = response.data;
      });

    document.title = "Daily Picture";
  },
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
  background-color: #2f2f2f;
}
.main {
  height: 90vh;
  width: 90vw;
  position: relative;
}
.d1 {
  position: absolute;
  background-size: 2500px 1300px;
  height: 30vh;
  width: 15vw;
  background-position: 0 50%;
  box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.8);
  top: 50%;
  transform: translateY(-50%);
  z-index: 2;
  animation: dd1 10s 1, dd12 10s 1;
  animation-delay: 4s, 14s;
}
.d2 {
  position: absolute;
  background-size: 2500px 1300px;
  height: 50vh;
  width: 25vw;
  background-position: -10vw 50%;
  left: 10vw;
  top: 50%;
  transform: translateY(-50%);
  z-index: 1;
  animation: dd2 10s 2;
  animation-delay: 4s;
}
.d3 {
  position: absolute;
  background-size: 2500px 1300px;
  overflow: hidden;
  height: 90vh;
  width: 40vw;
  left: 25vw;
  box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.8);
  background-position: -35vw 50%;
  top: 50%;
  transform: translateY(-50%);
  z-index: 3;
  animation: dd3 10s 2;
  animation-delay: 4s;
}
.d4 {
  position: absolute;
  overflow: hidden;
  background-size: 2500px 1300px;
  height: 80vh;
  width: 25vw;
  left: 60vw;
  background-position: -70vw 50%;
  top: 50%;
  transform: translateY(-50%);
  z-index: 1;
  animation: dd4 10s 2;
  animation-delay: 4s;
}
@keyframes dd1 {
  50% {
    width: 90vw;
  }
}
@keyframes dd12 {
  50% {
    background-position: Calc(-40vw) 50%;
  }
}
@keyframes dd2 {
  50% {
    background-position: Calc(-50vw) 50%;
  }
}
@keyframes dd3 {
  50% {
    background-position: Calc(-75vw) 50%;
  }
}
@keyframes dd4 {
  50% {
    background-position: Calc(-110vw) 50%;
  }
}
</style>
