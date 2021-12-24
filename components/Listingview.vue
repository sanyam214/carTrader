<template>
    <div class="listingContainer">
        <div v-if="isloading==false"  class="LeftSection">
            <ul>
                <li>
                   <img src="https://as2.ftcdn.net/jpg/00/95/60/61/500_F_95606194_TeneVz1Kdz2FyFRdYXUO4LAEoFJO5xdP.jpg" alt="">
                    <button v-on:click="showlistcars('Limosine')"><h5>Limousine</h5></button>
                </li>
                <li>
                   <img src="https://as2.ftcdn.net/jpg/00/95/60/61/500_F_95606194_TeneVz1Kdz2FyFRdYXUO4LAEoFJO5xdP.jpg" alt="">
                    <button v-on:click="showlistcars('C-class')">
                        <h5>C-class</h5>
                    </button>
                </li>
                <li>
                   <img src="https://as2.ftcdn.net/jpg/00/95/60/61/500_F_95606194_TeneVz1Kdz2FyFRdYXUO4LAEoFJO5xdP.jpg" alt="">
                    <button v-on:click="showlistcars('SUV Range')">
                         <h5>SUV Range</h5>
                    </button>
                </li>
                <li>
                   <img src="https://as2.ftcdn.net/jpg/00/95/60/61/500_F_95606194_TeneVz1Kdz2FyFRdYXUO4LAEoFJO5xdP.jpg" alt="">
                    <button v-on:click="showlistcars('Couples')">
                         <h5>Coupes</h5>
                    </button>
                </li>
                <li>
                   <img src="https://as2.ftcdn.net/jpg/00/95/60/61/500_F_95606194_TeneVz1Kdz2FyFRdYXUO4LAEoFJO5xdP.jpg" alt="">
                    <button  v-on:click="showlistcars('A class')">
                         <h5>A class/B class </h5>
                    </button>
                </li>
            </ul>
        </div>
        <div v-else>
                <b-spinner class="spinners" type="grow" label="Spinning"></b-spinner>
                <b-spinner class="spinners" type="grow" label="Spinning"></b-spinner>
                <b-spinner class="spinners" type="grow" label="Spinning"></b-spinner>
                <b-spinner class="spinners" type="grow" label="Spinning"></b-spinner>
                <b-spinner class="spinners" type="grow" label="Spinning"></b-spinner>
                <b-spinner class="spinners" type="grow" label="Spinning"></b-spinner>
        </div>
        <div v-if="zipsearch==false" class="RightSection">
           <ul>
               <li class="listItem" v-for="i in listitems" :key="i.vehicleID"> 
                   <NuxtLink class="carimg" :to="`/listing/${i.vehicleID}`" >
                       <!-- <img  :src="i.images" alt=""> -->
                         <Arrow-Corousel currentpage="listingpage" :interior="i.images" />
                       <div class="likes" @click="showModal">
                           <div class="heart">
                               <img src="https://www.flaticon.com/svg/vstatic/svg/3141/3141738.svg?token=exp=1619165798~hmac=13261c01e9403e2d1fc2809df2c6a9ee" alt="">
                           </div>
                           <div class="premium" v-if="i.Features.premium">Premium</div>
                        </div>
                   </NuxtLink>
                   <div class="Car-info" :to="`/listing/${i.vehicleID}`">
                       <h3>{{i.brandName}} {{i.vehicleIdentificationNumber}} {{i.modelName}}</h3>
                        <div class="rating">
                            <b-form-rating style="border:none; padding:0px" color="#0288d1" show-value>{{i.rating}}</b-form-rating>
                        </div>
                        
                        <h4><img src="https://www.flaticon.com/svg/vstatic/svg/25/25473.svg?token=exp=1619246188~hmac=b6e6bd326cc2683cddd4d7e9e81df306" style= "height:15px;width:20px;margin-bottom:0.3rem;" alt="">{{i.price}}/- onwards <h5>Show price in my city</h5></h4>
                        <h3 style="font-size:0.9rem; margin-top:0px; font-weight:400; margin-left:0.2rem">Avg. Ex-showroom price</h3>
                        <div class="extrafeatures">
                            <!-- <NuxtLink to="/alert" class="makeanoffer">Make an Offer</NuxtLink>  -->
                             <!-- <b-button style=" color:white;background-color:silver;margin-top: 7px; border: none;" @click="makeToast('success')">Make an offer</b-button> -->
                            <modal />
                            <img class="dollarimg" src="https://www.flaticon.com/premium-icon/icons/svg/3840/3840696.svg" alt="">
                            <h1 style="margin-left:0.5rem; margin-right:0.5rem; border-right:1px solid blue; margin-bottom:5px; padding-right:0.5rem;">Get Financing</h1>
                            <img class="getfinancinglogo" src="data:image/png;base64,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" alt="">
                            <img class="getsignatures" src="data:image/png;base64,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" alt="">
                        </div>
                   </div>
               </li>
           </ul>
           <nav aria-label="..." class="nav">
            <ul class="pagination">
                <li class="page-item disabled">
                <a class="page-link" href="#" tabindex="-1">Previous</a>
                </li>
                <li class="page-item"><button v-on:click="clickedbtn1" class="pagination-button">1</button></li>
                <li class="page-item active">
                <button v-on:click="clickedbtn2" class="pagination-button">2 <span class="sr-only">(current)</span></button>
                </li>
                <li class="page-item"><button v-on:click="clickedbtn3" class="pagination-button">3</button></li>
                <li class="page-item">
                <a class="page-link" href="#">Next</a>
                </li>
            </ul>
            </nav>
        </div>
        <div v-else class="RightSection">
           <ul>
               <li class="listItem" v-for="i in listofzipcode" :key="i.vehicleID"> 
                   <NuxtLink class="carimg" :to="`/listing/${i.vehicleID}`" >
                       <!-- <img  :src="i.images" alt=""> -->
                         <Arrow-Corousel currentpage="listingpage" :interior="i.images" />
                       <div class="likes" @click="showModal">
                           <div class="heart">
                               <img src="https://www.flaticon.com/svg/vstatic/svg/3141/3141738.svg?token=exp=1619165798~hmac=13261c01e9403e2d1fc2809df2c6a9ee" alt="">
                           </div>
                           <!-- <div class="premium" v-if="i.Features.premium">Premium</div> -->
                        </div>
                   </NuxtLink>
                   <div class="Car-info" :to="`/listing/${i.vehicleID}`">
                       <h3>{{i.brandName}} {{i.vehicleIdentificationNumber}} {{i.modelName}}</h3>
                        <div class="rating">
                            <b-form-rating style="border:none; padding:0px" color="#0288d1" show-value>{{i.rating}}</b-form-rating>
                        </div>
                        
                        <h4> <img src="https://www.flaticon.com/svg/vstatic/svg/25/25473.svg?token=exp=1619246188~hmac=b6e6bd326cc2683cddd4d7e9e81df306" style= "height:15px;width:20px;margin-bottom:0.3rem;" alt="">{{i.price}}/- onwards <h5>Show price in my city</h5></h4>
                        <h3 style="font-size:0.9rem; margin-top:0px; font-weight:400; margin-left:0.2rem">Avg. Ex-showroom price</h3>
                        <div class="extrafeatures">
                             <!-- <b-button style="margin-top: 7px;border: none; color:white; background-color:#c0c0c0" @click="makeToast('success')">Make an Offer</b-button> -->
                            <modal />
                            <img class="dollarimg" src="https://www.flaticon.com/premium-icon/icons/svg/3840/3840696.svg" alt="">
                            <h1 style="margin-left:0.5rem; margin-right:0.5rem; border-right:1px solid blue; margin-bottom:5px; padding-right:0.5rem;">Get Financing</h1>
                            <img class="getfinancinglogo" src="data:image/png;base64,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" alt="">
                             <img class="getsignatures" src="data:image/png;base64,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" alt="">
                        </div>
                   </div>
               </li>
           </ul>
           <nav aria-label="..." class="nav">
            <ul class="pagination">
                <li class="page-item disabled">
                <a class="page-link" href="#" tabindex="-1">Previous</a>
                </li>
                <li class="page-item"><button v-on:click="clickedbtn1" class="pagination-button">1</button></li>
                <li class="page-item active">
                <button v-on:click="clickedbtn2" class="pagination-button">2 <span class="sr-only">(current)</span></button>
                </li>
                <li class="page-item"><button v-on:click="clickedbtn3" class="pagination-button">3</button></li>
                <li class="page-item">
                <a class="page-link" href="#">Next</a>
                </li>
            </ul>
            </nav>
        </div>
    </div>
</template>`
<script>
    import { cardetails } from "@/assets/data.js"
    import {modal} from './modal'
    export default {
        props:['zipsearch'],
        data(){
            let listofzipcode=[];
            console.log("Initialisting is:",cardetails);
            if(this.$props.zipsearch!=false){
                for(let i in cardetails){
                    if(cardetails[i].zipcode==this.$route.query.zipcode){
                        console.log("Helloworls",i);
                        listofzipcode.push(cardetails[i]);
                    }
                }
            }
            return{
                listitems:cardetails,
                listofzipcode:listofzipcode,
                value:4,
                  show: false,
                    variants: ['primary', 'secondary', 'success', 'warning', 'danger', 'info', 'light', 'dark'],
                    headerBgVariant: 'dark',
                    headerTextVariant: 'light',
                    bodyBgVariant: 'light',
                    footerBgVariant: 'warning',
                    footerTextVariant: 'dark',
                    slide: 0,
                    sliding: null,
                    isloading:true,
                    loanRangeStep:10,
                    loanValue:200,
            }

        },
        created(){
            console.log("Created is called");
        },
        mounted(){
            this.isloading=false
            console.log("Mounted is called");
        },
        updated(){
            console.log("Hello World updated is called");
        },
        methods:{
            clickedbtn1(){
                let filtereditem=[];
                for(let i=0; i<4; i++){
                    filtereditem.push(cardetails[i]);
                }
                this.listitems=filtereditem;
            },
             typeinput(e) {
                 let percentage1 = (e.target.value/100)*100;
                 let percentage2 = 100-percentage1;
                 let mid= 100/2;
                 if(e.target.value>=mid){
                      this.$refs.sliderTrack.style.background = `linear-gradient(to right, green 0%, green ${percentage1}%, #fff ${percentage2}%, white 100%)`;
                 }
                 else{
                    this.$refs.sliderTrack.style.background = `linear-gradient(to left, white 0%, white ${percentage2}%, green ${percentage1}%, green 100%)`;  
                 }
                console.log(this.loanValue);
                    if (this.loanValue < 300) {
                         this.loanRangeStep = 10;

                    } else if (this.loanValue >= 300 && this.loanValue < 500) {
                         this.loanRangeStep = 50;
                    } else if (this.loanValue >= 500) {
                         this.loanRangeStep = 100;
                    } else {
                         this.loanRangeStep = 100;
                    }
                },
               makeToast(variant = null) {
                this.toastCount++
                this.$bvToast.toast(`Thanks for making an offer!!`, {
                title: 'Make an Offer',
                autoHideDelay: 5000,
                })
            },
            showlistcars(seleceteditem){
                  console.log("itemselected is:",seleceteditem);
                  let arr=[];
                for(let i in cardetails){
                    if(cardetails[i].brandName==seleceteditem || cardetails[i].modelName==seleceteditem){
                        if(this.$route.query.zipcode){
                            console.log("Limosine is clicked",this.$route.query.zipcode);
                            arr.push(cardetails[i]);
                        }
                        else{
                             console.log("Limosine is clicked",this.$route.query.zipcode);
                             arr.push(cardetails[i]);
                        }
                    }
                }
                if(!this.$route.query.zipcode){
                     this.listitems=arr;
                }
                else{
                    this.listofzipcode=arr;
                }
                
            },
             clickedbtn2(){
                let filtereditem=[];
                for(let i=4; i<8; i++){
                    filtereditem.push(cardetails[i]);
                }
                this.listitems=filtereditem;
            },
            clickedbtn3(){
                 let filtereditem=[];
                    for(let i=8; i<=8; i++){
                        filtereditem.push(cardetails[i]);
                    }
                this.listitems=filtereditem;
            },
            showModal() {
                    alert("Thanks for rating!!:)")
            },
            showModal() {
                if(this.input1=='' && this.input2==''){
                    alert("Please Enter Budget and carName")
                }
                else{
                     this.$refs['my-modal'].show();
                     this.input1='';
                     this.input2='';
                }
            },
            showModal2() {
                    alert("Thanks for Message to Dealer")
            },
            hideModal() {
                this.$refs['my-modal'].hide()
            },
            toggleModal() {
                this.$refs['my-modal'].toggle('#toggle-btn')
            },
            onSlideStart(slide) {
                this.sliding = true
            },
            onSlideEnd(slide) {
                this.sliding = false
            }
        }
    }
</script>

<style scoped>
 .listingContainer{
     width: 100%;
     height: auto;
     display: flex;
     flex-direction: row;
     align-items: flex-start;
     justify-content: space-around;
     flex-wrap: wrap;
 }
 .RightSection{
     width: 75%;
     height: 100%;
     background-color: #f7f7f7;

 }
  input {
    background: linear-gradient(to right, green 0%, green 50%, #fff 50%, #fff 100%);
    border: solid 1px #00b300;
    border-radius: 8px;
    height: 7px;
    width: 356px;
    outline: none; 
    transition:450ms ease-in;
    -webkit-appearance: none;
  }
  
   input::-webkit-slider-thumb {
    background-color: orange;
    border: solid 12px gold;
    border-radius: 0;
    height: 25px;
    width: 25px;
    border-radius: 50%;
    -webkit-appearance: none;
  }
 .getfinancinglogo{
     width: 5rem;
     height: 3rem;
     margin-top: 6px;
 }
 .getsignatures{
     width: 4rem;
     height: 100%;
     margin-top: 6px;
     margin-left: 1rem;
 }
 .spinners{
     margin-top: 100%;
 }
 .LeftSection{
     width: 25%;
     height: 100%;
     background-color: white;
     display: flex;
     justify-content: flex-start;
 }
 .LeftSection ul li{
     width:100%;
     height:3.2rem;
     display: flex;
     justify-content: flex-start;
     background-color: silver;
      /* background-color:rgb(35, 189, 228); */
      color:white;
 }
 .dollarimg{
     margin-left: 1rem;
     width: 20px;
     height: 20px;
     margin-top: 10px;
 }
 .LeftSection ul li img{
     width:20%;
     height:3rem;
 }
 .LeftSection ul li h5{
     font-size: 0.9rem;
     color: black;
     font-weight: bold;
     display: inline-block;
     margin-left:0rem;
 }
 .LeftSection ul li button{
     width: 100%;
     text-align: center;
     border: none;
     background-color: silver;
 }
 ul{
     height: auto;
     width:100%;
     list-style: none;
     margin: 0px;
     padding: 0px;
     display: flex;
     flex-direction: column;
     flex-wrap: wrap;
     justify-content: center;
     align-items: center;
     padding-top: 2rem;
 }
 .LeftSection ul{
     height: 25rem;
     width:100%;
     list-style: none;
     margin: 0px;
     padding: 0px;
     display: flex;
     flex-direction: column;
     flex-wrap: wrap;
     justify-content: space-between;
     padding: 2rem;
 }
 .listItem{
    width: 96%;
    height: 13rem;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: flex-start;
    flex-wrap: wrap;
    margin-bottom:1rem;
    text-decoration: none;
    background-color: white;
    border-right:2px solid silver;
    border-bottom:4px solid silver;
 }
 .listItem:hover{
     transform: scale(1.0.5);
 }
 .carimg{
     width: 39.2%;
     height: 100%; 
     display: flex;
     position:relative;
     flex-direction: row;
     justify-content: space-between;
     align-items: flex-start;
     flex-wrap: wrap;
 }
 .carimg img{
     background-size: 100% 100%;
 }
 .Car-info{
    width: 55%;
    height: 13rem;
    text-align: left;
    font-weight: bold;
 }
 .Car-info h3{
     margin-top:1rem;
     font-size: 1.5rem;
     color: #484848;
     font-weight: bold;
     font-family: sans-serif;
 }
 .Car-info h4{
     font-size:0.9rem;
     color: black;
     text-decoration: none;
     margin-top:1rem;

 }
 .Car-info h4 h5{
     color: #0288d1;
     font-size: 0.9rem;
     display: inline-block;
     font-weight: bold;
 }
 .carimg img{
     width: 100%;
     height: 100%;
 }
 .extrafeatures{
     display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    margin-top: 8px;
 }
 .Makeanofferbtn{
     display: inline-block;
     background-color: gold;
 }
 .headeritem{
     width: 100%;
     height: 100%;
     display: flex;
     flex-direction: row;
     align-items: flex-start;
     justify-content: space-between;
     flex-wrap: wrap;
     color: silver;
 }
 .getfinancing{
     width: 100%;
 }
 h1{
     color: #0288d1;
     font-size: 0.9rem;
     font-weight: bold;
     margin-top:1rem;
 }
 .rating{
     float: right;
     width:auto;
     height:auto;
     margin-top:0.6rem;
     color: green;
 }
 p{
     text-align: center;
 }
 .rating img{
     width:50%;
     height:100%;
 }
 .nav{
     margin-bottom:2rem;
 }
 .nav ul{
     flex-wrap: wrap;
    justify-content: flex-start;
 }
 .pagination-button{
    background-color: white;
    border: 1px solid silver;
    height: 2.3rem;
    width: 2rem;
 }
 .premium{
     display: inline-block;
 }
 .likes{
     position:absolute;
     padding:0.5rem 0.5rem;
     width:100%;
     height:2rem;
     display: flex;
     justify-content: space-between;
 }
 .heart img{
     width:1rem;
     height:1.5rem;
 }
 .heart{
     border-radius: 50%;
     background-color: silver;
     width:1.5rem;
     height:1.5rem;
 }
 .heart:hover{
     background-color: red;
 }
 .corousel-control-prev{
     height:2rem;
     margin-top:5rem;
 }
 .makeanoffer{
     background-color: silver;
     color: black;
     width:25%;
     padding:0.5rem 0.5rem;
     border-radius:10px;
     display:inline-block;
     text-align: center;
 }
 .car-info h1{
     display: inline-block;
     width:auto;
 }
 .pagination{
     flex-direction:row; 
     padding-top:0px;
     width:27%;
 }

  @media screen and (max-width: 850px) {
      .LeftSection{
          display: none;
      }
      .RightSection{
          width:100%;
      }
      .RightSection ul li{
          height:auto;
      }
      .carimg{
          width:100%;
      }
      .Car-info{
          width:100%;
          padding-left:0.5rem;
      }
      .getsignatures{
          display: none;
      }
      .pagination{
          width:100%;
      }
      @media screen and (max-width: 850px) {
          .Car-info h3{
              font-size:1rem;
          }
      }
  }
</style>