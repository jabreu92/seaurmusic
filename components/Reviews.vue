<template>
  <div>
    <b-container fluid>
      <h2>Customer Reviews</h2>
      <section v-if="errored">
        <p>
          We're sorry, we're not able to retrieve this information at the
          moment, please try back later
        </p>
      </section>
      <section v-else>
        <div v-if="this.loading">
          <p>One Moment... we are getting your request</p>
        </div>
        <div v-else>
          <div v-if="!this.loading">
            <ReviewCard
              v-for="reviewer in reviewers.results"
              :key="reviewer.login.uuid"
              :reviewpic="reviewer.picture.large"
              :reviewusername="reviewer.login.username"
            />
          </div>
        </div>
      </section>
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
        .get('https://randomuser.me/api/?results=7')
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

<style lang="scss" scoped></style>
