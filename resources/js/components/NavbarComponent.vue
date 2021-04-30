<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <a class="navbar-brand" href="#">Novus Logics</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="navbar-collapse collapse justify-content-end" id="navbar1" >
      <ul class="navbar-nav">
        <li v-if="auth===undefined" class="nav-item">
          <a class="nav-link"   href="/login">Login</a>
        </li>
        <li v-if="auth===undefined" class="nav-item">
          <a class="nav-link" href="/register">Register</a>
        </li>
        <li v-if="auth === 'LoggedIn'" class="nav-item">
          <a class="nav-link" href="/home">Profile</a>
        </li>
        <li v-if="auth === 'LoggedIn'" class="nav-item">
          <a class="nav-link" href="" v-on:click.prevent=logout>Logout</a>
        </li>

      </ul>
    </div>
  </nav>
</template>

<script>
   
    export default {
      data() {
        return {
          auth: undefined
        }
      },
      methods:{
        logout : function(event)  {
          localStorage.removeItem('usertoken')
          this.auth = undefined;
          window.location = "/login"
        }
      },
      mounted() {
        console.log(localStorage.usertoken);
        if(localStorage.usertoken != undefined){
          this.auth =  "LoggedIn";
        }

      }
    
    }

</script>