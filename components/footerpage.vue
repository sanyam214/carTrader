<template>
    <div class="footerContainer">
        <h2>Find cars For Sale On Cartrader</h2>
        <h3>Cartrader.com is the online source for all your motorcycle needs. Looking to sell a motorcycle? We can help. Place your motorcycle ad in front of millions of monthly visitors today. Ready to buy a cheap motorcycle or a motorcycle trailer? We can help with that too ― browse over 300,000 new and used motorcycles for sale nationwide from all of your favorite manufacturers like Harley-Davidson, Honda, Kawasaki, Suzuki, Yamaha, BMW, Victory, Ducati, Triumph, and KTM. You can easily estimate monthly payments, get insurance quotes, and set up price alerts for the bikes you’re interested in while you search. Make sure to follow us on social media for everything motorcycle, on and off the road!</h3>
        <div class="make-model">
            <ul>
                <h1>Top Car Makes</h1>
                <li><h4>Harley-Davidson</h4> <h5>30,025 Harley-Davidson motorcycles for sale</h5></li>
                <li><h4>BMW-123</h4> <h5>30 BMW-123 cars for sale</h5></li>
                <li><h4>BMW-XDF</h4> <h5>40,025 BMW-XDF cars for sale</h5></li>
                <li><h4>BMW-9Cd</h4> <h5>34,056 BMW-9Cd for sale</h5></li>
                <li><h4>GBF-BMW</h4> <h5>30,092 GBF-BMW cars for sale</h5></li>
                <li><h4>BVC-BMW</h4> <h5>025 BVC-BMW for sale</h5></li>
                <li><h4>BMW-987</h4> <h5>25 BMW-987 for sale</h5></li>
                <li><h4>BMW-1245</h4> <h5>300 BMW-1245 for sale</h5></li>
                <li><h4>BMW-456</h4> <h5>30,025 BMW-456 for sale</h5></li>
                <li><h4>BMW-9854</h4> <h5>305 BMW-9854 for sale</h5></li>
            </ul>
            <ul>
                <h1>Top Car Model</h1>
                <li><h4>Harley-Davidson</h4> <h5>30,025 Harley-Davidson motorcycles for sale</h5></li>
                <li><h4>BMW-123</h4> <h5>30 BMW-123 cars for sale</h5></li>
                <li><h4>BMW-XDF</h4> <h5>40,025 BMW-XDF cars for sale</h5></li>
                <li><h4>BMW-9Cd</h4> <h5>34,056 BMW-9Cd for sale</h5></li>
                <li><h4>GBF-BMW</h4> <h5>30,092 GBF-BMW cars for sale</h5></li>
                <li><h4>BVC-BMW</h4> <h5>025 BVC-BMW for sale</h5></li>
            </ul>
            <ul>
                <h1>Top Car Types</h1>
                <li><h4>BMW-9Cd</h4> <h5>34,056 BMW-9Cd for sale</h5></li>
                <li><h4>GBF-BMW</h4> <h5>30,092 GBF-BMW cars for sale</h5></li>
                <li><h4>BVC-BMW</h4> <h5>025 BVC-BMW for sale</h5></li>
            </ul>
            <ul>
                <h1>Top Car States</h1>
                <li><h4>Harley-Davidson</h4> <h5>30,025 Harley-Davidson motorcycles for sale</h5></li>
                <li><h4>BMW-123</h4> <h5>30 BMW-123 cars for sale</h5></li>
                <li><h4>BMW-XDF</h4> <h5>40,025 BMW-XDF cars for sale</h5></li>
                <li><h4>BMW-9Cd</h4> <h5>34,056 BMW-9Cd for sale</h5></li>
                <li><h4>GBF-BMW</h4> <h5>30,092 GBF-BMW cars for sale</h5></li>
                <li><h4>BVC-BMW</h4> <h5>025 BVC-BMW for sale</h5></li>
                <li><h4>Harley-Davidson</h4> <h5>30,025 Harley-Davidson motorcycles for sale</h5></li>
                <li><h4>BMW-987</h4> <h5>25 BMW-987 for sale</h5></li>
                <li><h4>BMW-1245</h4> <h5>300 BMW-1245 for sale</h5></li>
                <li><h4>BMW-456</h4> <h5>30,025 BMW-456 for sale</h5></li>
                <li><h4>BMW-9854</h4> <h5>305 BMW-9854 for sale</h5></li>
            </ul>
        </div>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style  scoped>
  .footerContainer{
      width: 100%;
      height: auto;
      background-color: black;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 2rem;
  }
  .footerContainer h2{
      font-size: 1.5rem;
      width: 100%;
      margin-top: 1rem;
      color: silver;
  }
  .footerContainer h3{
     font-size:1rem;
  }
  .footerContainer h3:hover{
     color: yellow;
  }
  .footer-img{
      width:30%;
      height:15rem;
  }
  .footer-img :hover{
      transform: scale(1.2);
  }
  .footer-img img{
      width:100%;
      height:100%;
  }
  .make-model{
      width:100%;
      height:auto;
      display: flex;
      flex-direction: row;
      justify-content: space-around;
      align-items: flex-start;
      flex-wrap: wrap;
      margin-top:2rem;
  }
  .make-model ul{
      width:23%;
      height: auto;
      margin: 0px;
      padding:0px;
  }
   .make-model ul li{
       margin: 0px;
      padding:0px;
      list-style: none;
      margin-left: 0.5rem;
      margin-bottom: 1rem;
      padding-top: 1rem;
   }
  .make-model ul h1{
      font-size: 2rem;
      color: silver;
  }
  h4{
      font-size: 1rem;
      color: yellow;
  }
  h5{
      font-size: 0.7rem;
      color: silver;
  }
  @media screen and (max-width: 700px) {
        .footerContainer h2{
            text-align: center;
            font-size: 1.5rem;
        }
        .footerContainer h3{
            text-align: center;
        }
        .make-model{
            flex-direction: column;
        }
        .make-model ul{
            width:100%;
        }
        .make-model ul h1{
            text-align: center;
            width: 100%;
            font-size: 1.5rem;
        }
        .make-model ul h4{
            text-align: center;
            width: 100%;
        }
        h5{
            width:100%;
            text-align: center;
        }
  }
</style>