<template>
    <div class="pd">
     <nav class="navbar navbar-expand-lg navbar-dark fixed-top" style="background-color: #521751;">
     <div class="container">
    <a class="navbar-brand" href="/"> <h3>Venus Blog</h3> </a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav ml-auto">
      <li class="nav-item active">
          <!-- <router-link to="/#" class="nav-link">Contact Us</router-link> -->
         <nuxt-link to="/addBlog" class="nav-link">Add Blog </nuxt-link>
        </li>
      <li class="nav-item active">
          <nuxt-link to="/contactUs" class="nav-link">Contact Us</nuxt-link>
        </li>
        <li class="nav-item active">
          <nuxt-link to="/community" class="nav-link">Join our Community</nuxt-link>
        </li>
    
    </ul>
    
  </div>
              </div>
  
</nav>
    </div>
</template>
<script>
export default {
    name : 'Navbar'
    
}
</script>

<style scoped>
.color{
color: white !important;
}
li a {
    text-decoration: none;
    color: white!important;
  }

  li a:hover,
  li a:active,
  li a.router-link-active {
    color: #fa923f !important;
  }
.pd{
  padding-top: 30px !important;
}
</style>>