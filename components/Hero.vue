<template>
        <div class="parent">
        <!-- <div class="HeroContainer">
             <img class="potrait" src="https://www.mercedes-benz.com/en/company/_jcr_content/root/slider/sliderchilditems/slideritem/image/MQ7-0-image-20191025121730/01-mercedes-benz-ag-company-3400x1440.jpeg" alt="">
        </div> -->
        <Corousel currentpage="Homepage" />
         <div class="inputs">
             <input class="searchtext" v-on:keyup.enter="submitform" v-model="zipcode" placeholder="Enter Zip code to search..." >
             <NuxtLink class="linking"  :to="`/listing?zipcode=${zipcode}`">
                 <img src="https://www.flaticon.com/svg/vstatic/svg/622/622605.svg?token=exp=1619233742~hmac=980e2c20fcb497c01c18de4c80dc4631" />
             </NuxtLink>
         </div >
        <!-- <div class="formWrapper">
            <form action="listing">
                <input type="text" class="locationinput" placeholder="Enter the location...">
                <input type="text" class="locationinput" placeholder="Enter the Zip code...">
                <button class="searchbtn" type="submit">Search</button>
            </form>
        </div> -->
   </div>
</template>

<script>
 import Corousel from "../components/Corousel"
    export default {
        name:"Hero",
        data(){
            return{
                zipcode:''
            }
        },
        components:{
            Corousel
        },
        methods:{
            submitform(){
               this.$router.push({path: '/listing?zipcode='+this.zipcode});
            }
        }
    }
</script>

<style scoped>
  .HeroContainer{
      width: 100%;
      height: 30rem;
  }
  .searchtext{
      width: 80%;
      border: 0px;
  }
  .potrait{
      width: 100%;
      height: 100%;
  }
  .inputs{
      width:60%;
      height:3rem;
      background-color: white;
      margin-top:-27rem;
      position: absolute;
      border-radius:15px ;
      margin-left:20%;
      display: flex;
      flex-direction: row;
      justify-content: space-evenly;
      flex-wrap: wrap;
  }
  input{
      outline: none;
  }
  .inputs .linking{
      width: 10%;
  }
  .linking img{
       height: 1.5rem;
        width: 2rem;
        margin-top: 17%;
        text-align: center;
  }
  .Search-btn{
      width:100%;
      height:3rem;
      border-radius:5px;
      border:none;
      background-color: black;
      color: white;
      text-align: center;
  }
    .inputs h1{
        font-size:1.7rem;
        padding:1rem 1rem;
    }
    .keyword{
        width:90%;
        height:3rem;
        border-radius:5px;
        border:1px solid silver;
        padding-left:0.5rem;
    }
    .ZIP, .Distance{
        width:42%;
        padding-left:0.5rem;
        height:3rem;
        border:1px solid silver;
    }
  .ab{
      padding: 1rem;
      width: 30%;
      border:2px solid cadetblue;
      position: absolute;
  }
  .formWrapper{
      width: 100%;
      height: 15rem;
      padding: 5rem;
  }
  .locationinput{
      padding: 1rem;
      width: 30%;
      border:2px solid cadetblue;
  }
  .searchbtn{
      width: 25%;
      padding: 1.1rem;
      border: none;
      background-color: orange;
      color: black;
  }
  
  @media screen and (max-width: 850px) {
      .inputs{
        width:90%;
        margin-top: 0rem;
        position: initial ;
        border-radius: 15px;
        margin-left: 0%;
        border:1px solid silver;
        margin:2rem 0rem;
      }
      .linking img{
          margin-top: 0.5rem;
      }
      .parent{
        justify-content: center;
        display: flex;
        flex-wrap: wrap;
      }
  }
  
</style>