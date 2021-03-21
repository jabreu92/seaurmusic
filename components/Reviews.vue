<template>
    <div>
        <b-container fluid>
        <h3>Customer Reviews</h3>
        <div v-if="!this.loading">
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
    data() {
        return {
            loading: true,
            errored: false,
            reviewers: []
        }
    },
     mounted () {
     axios
        .get('https://randomuser.me/api/?results=6')
        .then(response => { 
            this.reviewers = response.data
           
      
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


