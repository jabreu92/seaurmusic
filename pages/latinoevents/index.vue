<template>
  <div>
    <b-container fluid>
      <div v-if="!this.loading">
        <b-row>
          <b-col md="3" v-for="event in latinoevents" :key="event.id">
             <b-card bg-variant="secondary" text-variant="white"   :title="event.name" class="mt-1 mb-1 ">
              <BootstrapImage :image-src-url="event.images[0].url" /> 
              <b-card-text> Date: {{event.dates.start.localDate}} </b-card-text>
              <b-card-text> Time: {{event.dates.start.localTime}}</b-card-text>
              <b-button :href="event.url" target="_blank" variant="success">Click Here to Learn More </b-button>
              <template #footer>
                <small >Last Updated 3min ago</small>
              </template>
            </b-card>
          </b-col>
        </b-row>
      </div>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios'

 export default {
     data() {
        return {
            loading: true,
            items: null,
            errored: false,
            latinoevents: []
        }
    },
     mounted () {
    //let genre = this.$route.params.classificationId
    let genre = 'KnvZfZ7vAJ6'
    let url = `https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&source=ticketmaster&locale=*&countryCode=US&stateCode=WA&classificationName=music&classificationId=${genre}`

     axios
        .get(url)
        .then(response => {
            this.items = response.data
            this.latinoevents = this.items._embedded.events

               for (let i =0; i<this.latinoevents.length; i++){

                let event_image_array = this.latinoevents[i].images

                let filteredImagesArray = event_image_array.filter(function (el) {
                            return el.width == 640 && el.height == 360;
                 });
                this.latinoevents[i].images = filteredImagesArray
            }
            console.log(this.latinoevents)
        })
        .catch(error => {
            console.log(error)
            this.errored = true
            })
        .finally(() => this.loading = false)

        }
    }
</script>

<style></style>
