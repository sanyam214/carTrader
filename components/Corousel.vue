<template>
    <div>
        <div v-if="currentpage=='Homepage'">
            <b-carousel
            id="carousel-no-animation"
            style="text-shadow: 0px 0px 2px #000"
            no-animation
            indicators
            img-width="1200"
            img-height="300">
            <b-carousel-slide
            img-src="https://www.mercedes-benz.com/en/company/_jcr_content/root/slider/sliderchilditems/slideritem/image/MQ7-0-image-20191025121730/01-mercedes-benz-ag-company-3400x1440.jpeg">
            </b-carousel-slide>
            <b-carousel-slide
            img-src="https://www.mercedes-benz.com/en/company/_jcr_content/root/slider/sliderchilditems/slideritem/image/MQ7-0-image-20191025121730/01-mercedes-benz-ag-company-3400x1440.jpeg"
            ></b-carousel-slide>
            <b-carousel-slide
            img-src="https://www.mercedes-benz.com/en/company/_jcr_content/root/slider/sliderchilditems/slideritem/image/MQ7-0-image-20191025121730/01-mercedes-benz-ag-company-3400x1440.jpeg"
            ></b-carousel-slide>
                <b-carousel-slide
                    img-src="https://www.mercedes-benz.com/en/company/_jcr_content/root/slider/sliderchilditems/slideritem/image/MQ7-0-image-20191025121730/01-mercedes-benz-ag-company-3400x1440.jpeg"
                    ></b-carousel-slide>
                </b-carousel>
        </div>
    </div>
</template>

<script>
    export default {
        name:"Corousel",
        props:{
             interior: {
                type: Array,
                required: true
            },
            currentpage:{
                type:String,
                required:true
            }
        },
    }
</script>

<style scoped>

@media screen and (max-width: 700px) {
        .w-100{
            height:20rem;
        }
        .img-fluid{
            height:20rem;
        }
    }

</style>