<template>
    <div>
        <b-container fluid>
        <h3>Customer Reviews</h3>
        <div v-if="reviewers.results">
            <ReviewCard
                v-for="reviewer in reviewers.results"
                :key="reviewer.login.uuid"
                :review="reviewer"
            />
        </div>
        </b-container>
    </div>
</template>

<script>

import axios from 'axios'

    export default {
        data(){
            return {
                reviewers: []
            }
        },
        mounted (){
        axios
        .get('https://randomuser.me/api/?results=6')
        .then(response => { 
           this.reviewers = response.data
           console.log(this.reviewers)
      
        })
        .catch(error => {
            console.log(error)
            this.errored = true
            })
        .finally(() => this.loading = false)
            
        }
    
    }
</script>

<style lang="scss" scoped>
</style>