<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-dark bg-secondary">
      <router-link class="navbar-brand" to="/">Blog</router-link>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav">
          <router-link class="nav-item nav-link" to="/posts">Posts</router-link>
          <router-link class="nav-item nav-link" to="/add">Add post</router-link>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {

}
</script>