<template>
    <div>
        <div class="container mt-5 text-center" id="back">
            <h2 style="color:#521751">EST 2020</h2>
            <h1 style="color:white; letter-spacing:5px">#LAUNCH</h1>
            <p style="color:white; font-size:18px" >Join our community of like-minded developers, bloggers, designers & makers. <br> #Launch is a place to collaborate, discuss new products
               , find work, <br> get feedbacks or even find a co-founder.
            </p>
            <h5 style="color:#521751">READ THE FULL STORY <img src="@/assets/icons/arrow-right.svg"  width="20" height="20" title=""></h5>
            <div class="btn btn-secondary btn-lg" style="font-size:30px; background-color:#521751 !important">Join Now</div>
        </div>
        <div class="container mt-5">
            <div class="col-sm-3 layer2"></div>
                <h1 style="color:#521751">SOME OF OUR <br> MEMBERS</h1>
        </div>
        <div class="container">
        <div class="card-deck">
  <div class="card">
    <img src="@/assets/joe.jpg" class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title" style="font-size:40px">Ya Joe</h5>
      <p class="card-text">Ya Joe has a clothing company that focuses on the supply of casual menswear.</p>
    </div>
  </div>
  <div class="card">
    <img src="@/assets/whiteguy.png" class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title" style="font-size:40px">Barry Allen</h5>
      <p class="card-text">Barry Allen is a UI/UX designer and also owns a counsulting firm.</p>
    </div>
  </div>
  <div class="card">
    <img src="@/assets/ceo 2.jpg" class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title" style="font-size:40px">Edin Briston</h5>
      <p class="card-text">Edin Briston is an Android Developer that develops applications for devices that are powered by Android operating system.</p>
    </div>
  </div>
  </div>
</div>
    </div>

</template>

<script>
export default {
    
}
</script>

<style scoped>
#back{
    background-color: #fa923f!important;
}
.layer2{
    border: 4px solid #521751;
    width: 300px;
    height: 0px;
}
</style>