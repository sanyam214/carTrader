<template>
    <div class="parentContainer">
       <Listingview :zipsearch="zipcode" /> 
    </div>
</template>

<script>
    export default {
        data(){
          console.log("Zipcode is:",this.$route.query.zipcode);
          if(this.$route.query.zipcode!=undefined){
              return{
                zipcode:this.$route.query.zipcode
            }
          }
          else{
              return{
                zipcode:false
             }
          }
        }
    }
</script>

<style scoped>
.parentContainer {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  text-align: center;
  height: auto;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>