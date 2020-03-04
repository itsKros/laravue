<template>
  <div id="mainWrap">

      <!-- Main navigation starts-->
      <nav class="navbar navbar-expand-sm bg-dark navbar-dark">
        <div class="container-fluid">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link to="/" class="nav-link">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/create" class="nav-link">Create Post</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/posts" class="nav-link">Posts</router-link>
          </li>
        </ul>
        </div>
      </nav>
      <!-- Main navigation ends -->

      <!-- Content Starts -->
      <div class="py-5">
        <router-view></router-view>
      </div>
      <!-- Content ends -->
  </div>
</template>

<style>
    .fade-enter-active, .fade-leave-active {
      transition: opacity .5s
    }
    .fade-enter, .fade-leave-active {
      opacity: 0
    }
</style>

<script>
    export default{
    }
</script>