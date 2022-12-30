<template>
    <div class="overflow-scroll h-[100vh] bg-gray-800">
        <div class="relative  text-white">
            <img src="~/assets/images/moviebg.jpg" alt="image" />
            
            <div class="absolute top-12 left-10 md:left-28 md:top-28">
                <p class="uppercase text-red-500">Now Streaming</p>
                <p class="text-3xl"><span class="font-bold">Now</span>Streaming</p>
                <button class="bg-red-500  rounded-md mt-2 px-2 py-1">View Movies</button>
            </div>
        </div>
        <all-movies />
    </div>
</template>
<script>
import AllMovies from './AllMovies.vue'
export default{
  components: { AllMovies },
    name: "HomePage",
}
</script> 