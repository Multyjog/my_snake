<template>
  <div class="field">
    <div
      :class="{ snake: true }"
      v-for="(coord, index) in coords"
      :key="index"
      :style="{
        marginLeft: coord[0] * 40 + 'px',
        marginTop: coord[1] * 40 + 'px'
      }"
    ></div>
    <div
      :class="{ food: true }"
      :style="{
        marginLeft: foodCoords[0] * 40 + 'px',
        marginTop: foodCoords[1] * 40 + 'px'
      }"
    ></div>
  </div>
</template>

<script>
function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min;
}
export default {
  data: () => {
    return {
      coords: [
        [6, 8],
        [6, 9]
      ],
      foodCoords: [12, 14],
      direction: "ArrowUp",
      length: 2
    };
  },
  methods: {
    // esEqual(a) {
    //   for ( in this.coords) {
    //   }
    // },
    createFood() {
      const foodCoords = [getRandomInt(0, 20), getRandomInt(0, 20)];
      this.foodCoords = foodCoords;
    },
    updateHeadCoords() {
      let coords = [...this.coords];
      let head = [...this.head];
      if (this.direction === "ArrowUp") {
        head[1] -= 1;
        let newCoords = [head, ...coords];
        this.coords = newCoords.slice(0, this.length);
      }
      if (this.direction === "ArrowDown") {
        head[1] += 1;
        let newCoords = [head, ...coords];
        this.coords = newCoords.slice(0, this.length);
      }
      if (this.direction === "ArrowLeft") {
        head[0] -= 1;
        let newCoords = [head, ...coords];
        this.coords = newCoords.slice(0, this.length);
      }
      if (this.direction === "ArrowRight") {
        head[0] += 1;
        let newCoords = [head, ...coords];
        this.coords = newCoords.slice(0, this.length);
      }
    }
  },
  mounted() {
    document.addEventListener("keydown", e => {
      if (e.key === "ArrowUp") {
        this.direction = e.key;
      }
      if (e.key === "ArrowDown") {
        this.direction = e.key;
      }
      if (e.key === "ArrowLeft") {
        this.direction = e.key;
      }
      if (e.key === "ArrowRight") {
        this.direction = e.key;
      }
    });
    setInterval(() => {
      this.updateHeadCoords();
      this.createFood();
    }, 200);
  },
  computed: {
    head() {
      return this.coords[0];
    }
  }
};
</script>

<style scoped>
.field {
  width: 800px;
  height: 800px;
  background-color: rgb(240, 200, 140);
  left: 565px;
  position: absolute;
}
.snake {
  /* margin-top: 120px; */
  /* margin-left: 240px; */
  background-color: green;
  width: 40px;
  height: 40px;
  border-radius: 10px;
  position: absolute;
}
.food {
  margin-top: 120px;
  margin-left: 360px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: brown;
}
</style>
