<template>
  <div>
   <b-container fluid>
   <b-navbar toggleable="md" type="dark" variant="primary">
      <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
      <NuxtLink class="navbar-brand" to="/">SeaUrMusic</NuxtLink>
      <b-collapse is-nav id="nav_collapse">
        <b-navbar-nav>
           <NuxtLink to="/" class="nav-link">Events <span class="sr-only">(current)</span></NuxtLink>
           <NuxtLink to="/" class="nav-link">Blog <span class="sr-only">(current)</span></NuxtLink>
           <NuxtLink to="/" class="nav-link">FAQ <span class="sr-only">(current)</span></NuxtLink>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </b-container >
  </div>
</template>

<script scoped>
export default {
}
</script>

<style scoped>
  
</style>
