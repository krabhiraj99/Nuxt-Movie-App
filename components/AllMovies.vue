<template>
    <div>
        <div v-if="isLoading">
            <Loading />
        </div>
        <div v-if="!isLoading">
            <div class="flex justify-center mt-5 items-center">
                <input class="py-1 outline-none px-2 md:w-[300px] mr-3 rounded-md " v-model="searchInput" type="text" placeholder="Search Movie"/>
                <button @click="searchYourMovies" class="text-white mx-2  bg-red-500  rounded-md  px-4 py-1">Search</button>
                <button @click="clearInputData" class="text-white  bg-red-500  rounded-md  px-4 py-1">Clear</button>
    
            </div>
    
            <div class="text-white grid grid-cols-3 md:grid-cols-4 lg:grid-cols-5" >
                <div v-for="(movie, index) in movies" :key="index">
                    <single-movie :movie="movie" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import SingleMovie from './SingleMovie.vue';
import Loading from "./Loading.vue";
export default{
  components: { SingleMovie, Loading },
    name: "AllMovies",
    data(){
        return{
            movies: [],
            searchInput: "",
            isLoading: false,
        }
    },
    methods: {
        async fetchMovies(){
            this.isLoading=true;
            const res =  await this.$axios.get(`https://api.themoviedb.org/3/movie/now_playing?api_key=5678f61e286c7b5dff5a6c9fda1159f8&language=en-US&page=1`);
            this.movies=res.data.results;
            console.log(this.movies);
            this.isLoading=false;
        },

        async searchMovies(){
            this.isLoading=true;
            const res =  await this.$axios.get(`https://api.themoviedb.org/3/search/movie?api_key=5678f61e286c7b5dff5a6c9fda1159f8&language=en-US&page=1&query=${this.searchInput}`);
            this.movies=res.data.results;
            this.isLoading=false;  
        },

        clearInputData(){
            this.searchInput = "";
            this.fetchMovies();
        },

        searchYourMovies(){
            if(this.searchInput === ""){
                this.fetchMovies();
            }else{
                this.searchMovies();
            }
        },  
    },
    mounted(){
        this.fetchMovies();
    }
}
</script>

