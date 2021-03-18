<template>
  <div>
    <b-container fluid>
      <h3>Trending Music Events in Seattle</h3>
      <div v-if="!this.loading">
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
                loading: true,
                events: null,
                errored: false,
                arrayOfEvents: []
            }
        },

    mounted () {
    // USE THIS AS REFERENCE: https://www.ticketmaster.com/discover/concerts?classificationId=KnvZfZ7vAJ6&geoHash=c22y&radius=100&sort=date%2Casc&unit=miles&daterange=all
    //Endpoint: Gell all concerts in WA: https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&locale=*&page=1&countryCode=US&stateCode=WA&classificationName=music
    //Endpoints: Get all Concerts Events in WA https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&locale=*&page=1&countryCode=US&stateCode=WA&classificationName=music
    //Endpoints: Get all Latin Concerts Events in WA https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&locale=*&countryCode=US&stateCode=WA&classificationName=music&classificationId=KnvZfZ7vAJ6
    //Endpoint get all metal concerts: https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&locale=*&countryCode=US&stateCode=WA&classificationName=music&classificationId=KnvZfZ7vAvt
    //Endpoint: Get an event: 
    //FAQ Make question & prompt who made website show info

     axios
        .get('https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&locale=*&countryCode=US&stateCode=WA&classificationName=music&classificationId=KnvZfZ7vAJ6')
        .then(response => { 
            this.events = response.data
            console.log(this.events)  
            this.arrayOfEvents = this.events._embedded.events // if the ._embedded.events does not exist in the response data dont proceed.
        })
        .catch(error => {
            console.log(error)
            this.errored = true
            })
        .finally(() => this.loading = false)
            
        }

    }

</script>

<style scoped></style>
