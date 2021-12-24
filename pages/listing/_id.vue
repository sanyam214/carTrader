<template>
    <div class="selecteditem">
        <div v-if="itemchoosen" class="Leftsection">
            <div>
                <span class="info">
                    <Arrow-Corousel currentpage="selecteditempage" :interior="itemchoosen.images" />
                    <h1>{{itemchoosen.brandName}} {{itemchoosen.modelName}}</h1>
                    <h2> Rs.{{itemchoosen.price}}/- <h3 class="emi">Get a best offer now!</h3></h2>
                    <h2> EMI starts at:-</h2>
                    <h3 class="emi"> Rs.67613/- / Month</h3>
                    <h4>Interest calculated at 9.8% for 60 months</h4>
                    <h2>Key Specs of {{itemchoosen.brandName}} {{itemchoosen.modelName}}:-</h2>
                    <b-table striped hover :items="items" style="border:1px solid silver;"></b-table>
                    <button class="latest-offers">View Latest Offers</button>
                    <h5>Don't miss out on the best offers for this month</h5>
                </span>
            </div>
        </div>
        <div class="Rightsection">
            <div class="best-offers-search">
                <h1 class="offers-h1">Find your right car</h1>
                <div style="background-color:#24272c;color:#fff;">New car</div>
                <div style="color:black;">Used car</div>
                <input type="number" placeholder="Enter Budget" id="budget" v-model="input1">
                 <input type="text" placeholder="Enter CarName" id="budget" v-model="input2">
                 <!-- <button class="latest-offers">Search</button> -->
                  <button id="show-btn" @click="showModal">Make an Offer</button>
                    <b-modal ref="my-modal" hide-footer title="Make an Offer">
                    <div class="message-container">
                        <div class="text-container">
                             <p>Thanks for making an offer with us. Our Dealer will be soon in touch with you.</p>
                        </div>
                        <h6>Message To Dealer</h6>
                        <textarea placeholder="I would like to make an offer on your Mercedies" cols="50" rows="10">
                        </textarea>
                       <b-button variant="success" @click="makeToast('success')" class="modalbtnssubmit">Submit</b-button>
                    </div>
                    </b-modal>
                 <h4>Advanced Offers Available!!</h4>
            </div>
        </div>
    </div>
</template>

<script>
   import { mapGetters } from 'vuex'
   import {mapMutations} from "vuex"
    export default {
        props: ['product'],
        data(){
            return{
                input1:'',
                input2:'',
                items: [
                    { Features: "Colour", Description: 'White' },
                    { Features: 'Fuel TYpe', Description: 'Diesel' },
                    { Features: 'Air Conditioning', Description: 'True' },
                    { Features: 'Price', Description: '170000000' }
                ],
                 slide: 0,
                 sliding: null
            }
        },
        computed: {
            itemchoosen() {
                return this.$store.getters.getProductById(this.$route.params.id);
            }
        },
         methods: {
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
             makeToast(variant = null) {
                this.$bvToast.toast('Thanks for making an Offer', {
                title: `Offer is Made Successfully`,
                variant: variant,
                solid: true
                })
                this.$refs['my-modal'].hide()
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

<style  scoped>
  .selecteditem{
      width: 100%;
      height: 68rem;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: flex-start;
      flex-wrap: wrap;
  }
  .Leftsection{
      width: 60%;
      height:auto;
      padding-left:1rem;
      padding-top:1rem;
  }
  .Rightsection{
      width: 35%;
      height:57rem;
      padding-left:1.5rem;
  }
  .carimg{
      width: 100%;
      padding: 0.5rem;
  }
  h1{
    color: #24272c;
    font-weight: 500;
    font-size: 24px;
    margin-top:1rem;
}
  #show-btn, .latest-offers{
    background: #f75d34;
    color: #fff;
    font-size: 17px;
    line-height: 47px;
    height: 48px;
    width: 100%;
    border: 0;
    -webkit-border-radius: 4px;
    border-radius: 4px;
    cursor: pointer;
    text-align: center;
    max-width: 320px;
    margin-bottom: 10px;
    margin-top:2rem;
  }
  .emi{
      font-size: 17px;
      padding:0rem 0.5rem;
      font-weight: 600;
      background-color: #f75d34;;
      color: #fff;
      border-radius:10px;
      margin-bottom:0.5rem;
  }
  h3{
      font-size: 17px;
      color: #0288d1;;
      font-weight: 600;
  }
  h2{
      font-size:1.2rem;
      margin-bottom:1rem;
  }
  h5{
      font-size:0.7rem;
  }
  h4{
      font-size:1rem;
  }
  .features{
      width:100%;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      padding-right:1rem;
  }
  .features>div{
      width:15%;
      height:100%;
  }
  .best-offers-search{
    width: 348px;
    height: 443px;
    border-radius: 5px;
    box-shadow: 0 0 70px 0 rgb(36 39 44 / 30%);
    background: #fff;
    padding: 19px 24px;
    z-index: 100;
    margin-top:1rem;
  }
  .best-offers-search>div{
      width:8rem;
      height:3rem;
      border-radius: 5px;
      border:1px solid black;
      display: inline-block;
      text-align: center;
      padding-top:0.6rem;
      margin-top:1rem;
  }
  .best-offers-search>input{
      width:100%;
      height:10%;
      margin-top:1.5rem;
      
  }
  .best-offers-search>h4{
     float: right;
     margin-top:2rem;
     font-size:0.7rem;
      
  }
  .offers-h1{
      margin-top:0px;
    font-size: 30px;
    font-weight: 700;
  }
  .message-container{
      text-align: center;
  }
  .message-container p, h6{
      text-align: left;
  }
    .modalbtnssubmit{
        background: #f75d34;
        color: #fff;
        font-size: 17px;
        line-height: 47px;
        padding-top: 2px;
        height: 48px;
        width: 100%;
        border: 0;
        border-radius: 4px;
        cursor: pointer;
        text-align: center;
        max-width: 320px;
        margin-bottom: 10px;
        margin-top: 2rem;
    }

    @media screen and (max-width: 850px) {
        .Rightsection{
            width:100%;
            height:auto;
            margin:2rem 0rem;
            padding:0px;
            display: flex;
            justify-content: center;
        }
        .Leftsection{
            width: 90%;
            padding-left: 0px;
        }
        .selecteditem{
            align-items: center;
            justify-content: center;
            height: auto;
            flex-direction: column;
        }
        .Leftsection>div{
            align-items: center;
        }
        
        h1, h2, h4{
            width:100%;
            text-align: left;
        }
        .latest-offers{
            width:100%;
        }
        textarea{
                padding: 0rem;
              width: 99%;
        }
    }
</style>