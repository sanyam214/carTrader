<template>
    <div class="navContainer">
        <div class="carLogo">
            <div class="brand-logo">
                 <img class="Logo" src="https://yt3.ggpht.com/ytc/AAUvwniyWsVZwP356ENZnxUYchY4e7R-aAs0l2mbVVzHaT0=s900-c-k-c0x00ffffff-no-rj" alt="">
                 <h3>Cartrader</h3>
            </div>
             <div class="burger-bar">
                 <img v-on:click="showmenu" class="menubar" src="https://www.flaticon.com/svg/vstatic/svg/561/561123.svg?token=exp=1619433135~hmac=37effc31bef76e13d862c38dead83e62" alt="">
             </div>
             <ul class="listContainer">
                <li>
                    <NuxtLink class="linking" to="/">Home</NuxtLink>
                </li>
                <li> <NuxtLink class="linking" to="/listing">Listings</NuxtLink></li>
                <li> <NuxtLink class="linking" to="/">Seller</NuxtLink></li>
                <li> <NuxtLink class="linking" to="/">Buyer</NuxtLink></li>
                <li> <NuxtLink class="linking" to="/">CarService</NuxtLink></li>
            </ul>
            
        </div>
        <!-- <button class="offerbtn">Offers/cashback</button> -->
    </div>
</template>

<script>
   import Vue from 'vue';
    export default {
        data () {
      return {
        renderComponent: true,
        showlist:false
      };
    },
        methods: {
        forceRerender () {
            // remove the my-component component from the DOM
            this.renderComponent = false;

            this. $nextTick (() => {
            // add my-component component in DOM
            this.renderComponent = true;
            });
        },
     
        }
    }
</script>

<style>
   .navContainer{
       width: 100%;
       height: auto;
       display: flex;
       flex-direction: column;
       align-items: flex-start;
       border: 2px solid black;
       background-color: black;
   }
   .burger-bar{
       display: none;
   }
   .linking{
       color: silver;
   }
   .listContainer{
       margin: 0px;
       padding-left: 16px;
       margin-left: 17rem;
       width: 50%;
       display: flex;
       cursor: pointer;
       flex-direction: row;
       flex-wrap: wrap;
       justify-content: flex-end;
       color: rgb(226, 226, 226);
       list-style: none;
       font-size: 1rem;
   }
   .listContainer li{
       margin-left:2rem;
   }
   h3{
       color: silver;
       margin-bottom: 1px;
       display: inline-block;
   }
   .offerbtn{
       padding: 1rem;
       background-color: orange;
       color: white;
       width: 25%;
   }
   .Logo{
       width: 6rem;
       height: 100%;
       margin-right:1rem;
   }
   .carLogo{
       width: 100%;
       display: flex;
       align-items: center;
       justify-content: flex-start;
       padding-left: 2rem;
       color: silver;
       height: 5rem;
   }
   .searchLogo{
       width: 2%;
       position: absolute;
       color: white;
   }
   .menubar{
       display: none;
   }
    .brand-logo img{
        margin-right:0rem;
    }
    .brand-logo h3{
        margin-top: 1rem;
    }
   @media screen and (max-width: 700px) {
       .listContainer{
           display: none;
       }
       .menubar{
           width: 1rem;
           height: 1rem;
           display: inline-block;
           background-color: white;
           right: 0;
       }
       .Logo {
        width: 3rem;
        height: 3rem;
        margin: 0rem;
       }
       .carLogo{
           padding: 0.5rem;
           justify-content: space-between;
       }
       h3{
            font-size: 1.5rem;
       }
       .burger-bar{
           display: inline-block;
           height:auto;
       }
       .burger-bar img{
           float:right;
       }
       .brand-logo h3{
            margin-top:0.5rem;
       }
   }
</style>