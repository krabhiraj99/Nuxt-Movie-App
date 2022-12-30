<template>
    <div class="bg-gray-800 h-[100vh]">

        <div class="flex ml-5 md:m-auto pt-20 md:mt-30 max-w-[1000px] ">
          <div>
            <img
              class="image cursor-pointer w-[230px] rounded-md"
              :src="`https://image.tmdb.org/t/p/w500/${movie?.poster_path}`"
              :alt="`${movie?.poster_path}`"
            />
          </div>

          <div class="text-white ml-5 max-w-[350px] md:max-w-[500px]">
            <p class="font-bold text-2xl">Title: {{movie?.original_title}}</p>
            <div class="text-sm mt-2"><span class="italic underline mr-1">Released On:</span> {{movie?.release_date}}</div>
            <div class="text-sm mt-2"><span class="italic underline mr-2">Duration:</span>{{movie?.runtime}} minutes</div>
            <div class="text-sm mt-2"><span class="italic underline mr-2">Revenue:</span>${{movie?.revenue}}</div>
            <div class="text-sm mt-2"><span class="italic underline mr-2">Overview:</span>{{movie?.overview}}</div>

          </div>
        </div>
    </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      movie: undefined,
    };
  },

  methods: {
    async fetchCurrentMovie() {
      const res = await this.$axios.get(
        `https://api.themoviedb.org/3/movie/${this.$route.params.movieid}?api_key=5678f61e286c7b5dff5a6c9fda1159f8&language=en-US`
      );
      console.log("Current Movie Data", res.data);
      this.movie = res.data;
    },
  },

  async mounted() {
    await this.fetchCurrentMovie();
  },
};
</script>

<!-- `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=37ed43a4f8eaa2abd75f9283692947bc&language=en-US` -->
<!-- :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`" -->
