<template>
  <div>
    <b-container fluid>
      <b-jumbotron
      bg-variant="dark"
      text-variant="white"
      border-variant="dark"
      class="mb-0 mt-0"
      >
        <template #header>Seaurmusic </template>
        <template #lead>
          Seattle's #1 Music Event Provider
        </template>
        <hr class="my-4" />
         <NuxtLink to="/" class="nav-link"> <span class="sr-only">(current)</span><b-button variant="primary"> Start Seeing Events </b-button></NuxtLink>
      </b-jumbotron>
    </b-container>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>

 .image {
        
        margin-left: 5rem;
    }
</style>
