<template>
  <div>
    
    <Hero />
    <Nav />
    <Nuxt />
    <BottomNav />
    <BottomHero />
  
  </div>
</template>
<script>
export default {
  head: {
    title: 'SeaUrMusic',
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      {
        hid: 'description',
        name: 'description',
        content: 'SeaUrMusic, Seattle #1 Music Event Provider from layout'
      }
    ],
    link: [{ rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }]
  }
}
</script>


<style>


</style>
