<template>
<div id="app">
<div id="menu">
<nav class="my-navbar navbar navbar-expand-lg">
<a class="navbar-brand" href="#"></a>
<button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
  <span class="navbar-toggler-icon">&#9662;</span>
</button>

<div class="collapse navbar-collapse" id="navbarSupportedContent">
  <ul class="navbar-nav mr-auto">
    <li class="nav-item active">
    <router-link to="/">
      <a class="nav-text nav-link" href="#">Home<span class="sr-only">(current)</span></a>
    </router-link>
    </li>
    <li class="nav-item">
    <router-link to="/browse">
      <a class="nav-text nav-link" href="#">Shop</a>
    </router-link>
    </li>
    <li class="nav-item">
    <router-link to="/admin">
      <a class="nav-text nav-link" href="#">Admin</a>
    </router-link>
    </li>
  </ul>
  <router-link to="/cart">
     <div class="menu-item">
     <i class="nav-pic fas fa-shopping-cart"></i>
     <p class="nav-pic">{{cart}} items</p>
     </div>
  </router-link>
</div>
</nav>
<div class="home">
  <router-link to="/">
    <img class="logo" src="/images/logo.png">
  </router-link>
</div>
</div>
<router-view />

</div>
</template>
<script>
export default {
computed: {
  cart() {
    try {
      return this.$root.$data.cart.length;

    } catch (error) {
      return 0;
    }
  }
},
}
</script>
<style>
* {
  box-sizing: border-box;

}
#app {
  margin-bottom: 40px;
}

@media only screen and (max-width: 450px) {
  .nav-text {
    color: #FFFFFF;
  }
  .nav-pic {
    color: #FFFFFF;
  }
  .logo {
    width: 50%;
    height: default;
    margin-left: 25%;
    margin-top: 10px;
  }
}

@media only screen and (min-width: 961px) {
  .nav-text {
    color: #FFFFFF;
    }
  .nav-pic {
    color: #da982c;
  }
  .logo {
    width: 15%;
    hieght: default;
    margin-left: 42.5%;
    margin-top: 10px;

  }
}

body {
  background-color: #ffa1b5;
}
.my-navbar {
  background: linear-gradient(80deg, #F96988 20%, #FFFFFF 80%);
}

/* Footer */
.footer {
  height: 50px;
  padding: 20px 100px 0px 100px;
  background: #e3e3e3;
  font-size: 12px;
}

.footer a {
  color: #000;
}

h1 {
  font-size: 20px;
}

h2 {
  font-size: 14px;
}
</style>
