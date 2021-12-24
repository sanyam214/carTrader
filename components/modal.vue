<template>
    <div>
         <button class="modalbtns" id="show-btn" @click="showModal">Make an Offer</button>
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
    </div>
</template>

<script>
    export default {
        name:"modal",
        methods:{
               showModal() {
          
                     this.$refs['my-modal'].show();
            },
            makeToast(variant = null) {
            this.$bvToast.toast('Thanks for making an Offer', {
            title: `Offer is Made Successfully`,
            variant: variant,
            solid: true
            })
            this.$refs['my-modal'].hide()
        },
            hideModal() {
                this.$refs['my-modal'].hide()
            },
            toggleModal() {
                this.$refs['my-modal'].toggle('#toggle-btn')
            },
        }
    }
</script>

<style scoped>
    .modalbtns{
        border: none;
        background-color: silver;
        color: white;
        margin-top: 12px;
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
        margin-left: 15%;
    }

     @media screen and (max-width: 850px) {
         textarea{
             width:100%;
         }
         .modalbtnssubmit{
             margin:0px;
             padding:0px;
         }
         .message-container{
             text-align: center;
         }
         .modalbtns[data-v-0f226802]{
             font-size:0.7rem;
         }
     }

</style>