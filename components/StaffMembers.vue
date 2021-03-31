<template>
  <div>
    <b-container fluid>
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
        <h1 class="title">{{ title }}</h1>
          <div v-if="!this.loading">
            <b-row>
              <b-col md="3" v-for="index in 4 " :key="index">
                <StaffMemberCard
                  v-for="staffmember in staffmembers.results"
                  :key="staffmember.login.uuid"
                  :staffFullName="staffmember.name.first + staffmember.name.last"
                  :staffPic="staffmember.picture.large"
                  :staffEmail="staffmember.email"
                  :staffPhone="staffmember.phone"
                  :staffHometown="staffmember.location.country"
                  :staffAge="staffmember.dob.age"
                />
              </b-col>
            </b-row>
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
            staffmembers: [],
            title: 'SeaUrMusic Staff'

        }
    },
    head() {
      return {
        title: this.title,
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {
            hid: 'faq-id',
            name: 'description',
            content: 'FAQ Page'
          }
        ]
      }
    },
     mounted () {
     axios
        .get('https://randomuser.me/api/?results=2')
        .then(response => {
            this.staffmembers = response.data
            console.log(this.staffmembers)
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
