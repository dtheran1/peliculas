<template>
  <div class="card" :class="{ 'movie-like': like }">
    <img class="card-img-top" :src="movie.cover" :alt="movie.title" />
    <div class="card-body">
      <h2 class="card-title">{{ movie.title }}</h2>
      <p class="card-text">
        {{ movie.synopsis }}
      </p>
      <button
        class="btn"
        :class="btnStatus"
        @click="toggleLike"
        v-text="like ? 'Favorita' : 'Agregar a Favoritas'"
      ></button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "Hola soy el mensaje de movieComp",
    };
  },

  props: {
    movie: {
      type: Object,
      required: true,
    },
    like: {
      type: Boolean,
      required: true,
      default() {
        return false;
      },
    },
  },
  methods: {
    toggleLike() {
      let data = {
        id: this.movie.id,
        like: !this.movie.like,
      };
      this.$emit("toggleLike", data);
    },
  },
  computed: {
    btnStatus() {
      return this.like ? "btn-like" : "btn-light";
    },
  },
};
</script>

<style>
</style>