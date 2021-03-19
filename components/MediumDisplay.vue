<template>
<div>
    <b-container fluid>
     <b-row>
       <b-col lg="12">
           <DeckCards />
        </b-col>
    </b-row>
    </b-container>   
</div>
  
</template>

<script>
import DeckCards from './DeckCards.vue'

export default {
  components: { DeckCards },
   

}
</script>

<style scoped>

   
</style>