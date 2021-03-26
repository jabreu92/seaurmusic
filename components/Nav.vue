<template>
  <div>
    <b-container fluid>
      <b-navbar toggleable="md" type="dark" variant="primary" class="mb-0 mt-0">
        <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
        <NuxtLink class="navbar-brand" to="/">Home</NuxtLink>
        <b-collapse is-nav id="nav_collapse">
          <b-navbar-nav>
            <NuxtLink to="/events" class="nav-link"
              >Events <span class="sr-only">(current)</span></NuxtLink
            >
            <NuxtLink to="/staff" class="nav-link"
              >Staff <span class="sr-only">(current)</span></NuxtLink
            >
            <NuxtLink to="/faq" class="nav-link"
              >FAQ <span class="sr-only">(current)</span></NuxtLink
            >
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </b-container>
  </div>
</template>

<script scoped>
export default {
}
</script>

<style scoped>

  .navbar {
    border-radius: 5px;
  }



</style>
