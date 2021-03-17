<template>
  <div>
    <b-container fluid>
      <h3>Trending Music Events in Seattle</h3>
      <div>
        {{events}}
      </div>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios'

export default {
        data(){
            return {
                events: null,
                errored: false
            }
        },

    mounted () {
     axios
        .get('https://app.ticketmaster.com/discovery/v2/events.json?classificationName=music&dmaId=324&apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw')
        .then(response => (this.events = response.data))
        .catch(error => {
            console.log(error)
            this.errored = true
            })
        .finally(() => this.loading = false)
        
        }

    }

</script>

<style scoped></style>
