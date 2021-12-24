<template>
    <div>
        <div v-if="currentpage!='listingpage'">
             <b-carousel
                    id="carousel-1"
                    v-model="slide"
                    :interval="4000"
                    controls
                    indicators
                    background="#ababab"
                    img-width="1024"
                    img-height="480"
                    style="text-shadow: 1px 1px 2px #333;"
                    @sliding-start="onSlideStart"
                    @sliding-end="onSlideEnd"
                    >
      <!-- Text slides with image -->
                <b-carousel-slide v-for="i in interior" :key="i"
                        :img-src="i"
                ></b-carousel-slide>

      
             </b-carousel>

        </div>
        <div v-if="currentpage=='listingpage'">
             <b-carousel
                    id="carousel-1"
                    v-model="slide"
                    :interval="200000"
                    controls
                    indicators
                    background="#ababab"
                    img-width="1024"
                    img-height="480"
                    position="relative"
                    >
      <!-- Text slides with image -->
                <b-carousel-slide v-for="i in interior" :key="i"
                        :img-src="i"
                ></b-carousel-slide>

      
             </b-carousel>

        </div>
        
    </div>
</template>

<script>
    export default {
        name:'Arrow-Corousel',
        props:{
            interior: {
                type: Array,
                required: true
            },
             currentpage:{
                type:String,
                required:true
            }
        }
    }
</script>

<style scoped>
    .corousel-control-prev a{
        height:2rem;
        margin-top:5rem;
    }
</style>