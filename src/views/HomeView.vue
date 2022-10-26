<script>
export default {
  data() {
    return {
      imgRef: null,
    };
  },
  mounted() {
    this.getRandomDuck();
  },
  methods: {
    getRandomDuck() {
      fetch("https://random-d.uk/api/v1/random")
        .then((resp) => resp.json())
        .then((data) => {
          console.log(data);
          this.imgRef = data.url;
        });
    },
  },
};
</script>

<template>
  <main>
    <img
      v-if="imgRef"
      :src="imgRef"
      alt="this is a random duck!"
      height="300"
    />
    <button @click="getRandomDuck">Get Random Duck!</button>
  </main>
</template>
