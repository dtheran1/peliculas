<template>
  <div class="container">
    <h1>Peliculas</h1>
    <div class="row">
      <div
        class="col-12 col-md-6 col-lg-4"
        v-for="movie in movies"
        :key="movie.id"
      >
        <MovieComp
          :movie="movie"
          :like="movie.like"
          @toggleLike="onToggleLike"
        />
      </div>
    </div>

    <MovieFav v-if="showFav" @hideFav="onHideFav" ref="movieFav" />
  </div>
</template>

<script>
import MovieComp from "@/components/MovieComp";
import MovieFav from "@/components/MovieFav";
export default {
  components: {
    MovieComp,
    MovieFav,
  },
  data() {
    return {
      showFav: false,
      movies: [
        {
          id: 1,
          title: "Titanic",
          synopsis:
            "Durante las labores de recuperación de los restos del famoso trasatlántico Titanic, una anciana norteamericana se pone en contacto con la expedición para acudir…",
          cover:
            "https://image.tmdb.org/t/p/w185_and_h278_bestv2/zraTDtulFw2wrpyuYf646k95MNq.jpg",
          like: false,
        },
        {
          id: 2,
          title: "El Rey León",
          synopsis:
            "Un remake del clásico animado de Disney de 1994 El rey león que estará dirigido por Jon Favreu. Simba (Donald Glover) es el hijo del rey de los leones, Mufasa…",
          cover:
            "https://image.tmdb.org/t/p/w185_and_h278_bestv2/3A8ca8WOBacCRujSKJ2tCVKsieQ.jpg",
          like: false,
        },
        {
          id: 3,
          title: "Toy Story",
          synopsis:
            "Otra divertidísima aventura de Pixar, pese a no llegar al nivel de sus predecesoras",
          cover: "https://i.blogs.es/a34e58/cartel-toy-story-4/840_560.jpg",
          like: false,
        },
      ],
    };
  },
  methods: {
    onToggleLike(data) {
      let movieLike = this.movies.find((movie) => movie.id == data.id);
      movieLike.like = data.like;
      this.showFav = data.like;
    },
    onHideFav(show) {
      this.showFav = show;
    },
  },
};
</script>

<style>
</style>