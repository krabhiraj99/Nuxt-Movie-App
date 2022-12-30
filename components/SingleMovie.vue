<template>
    <div class="flex flex-col text-center justify-center my-4">
        <div class="relative flex justify-center">
                <nuxt-link :to="'movies/' + movie.id">
                <img 
                class="image cursor-pointer  w-[170px]  rounded-md"
                :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`"
                :alt="`${movie.poster_path}`"
                />
                <p  class="showOnHover absolute w-[170px] text-sm bottom-0 pb-2 rounded-b-md bg-red-500">{{movie.overview.slice(0,150)}} <span v-if="movie.overview.length > 200">...</span></p>
            </nuxt-link>
                <p class=" absolute left-5 md:left-6 lg:left-10 bg-red-500 rounded-br-lg rounded-tl-md w-7 p-1 text-white leading-none">{{movie.vote_average}}</p>
            </div>
        <p class="cursor-pointer">{{movie.original_title}}</p>
    </div>
</template>

<script>
export default {
    name: "SingleMovie",
    props:{
        movie: Object,
    },
    data(){
        return{
            showOverview:false,
        }
    },
    mounted(){
        console.log("Movie", this.movie);
    }
}
</script>
<style scoped>
.showOnHover{
    display: none;
    transition: ease-in-out 500ms;
}
.image:hover + .showOnHover{
    display: block;
    color: white;

}

</style>