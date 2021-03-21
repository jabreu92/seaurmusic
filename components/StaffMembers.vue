<template>
    <div>
        <b-container fluid>
        <h3>The Staff</h3>
        <div v-if="!this.loading">
         <b-row>
          <b-col md="3" v-for="index in 4 " :key="index">
            <StaffMemberCard
                v-for="staffmember in staffmembers.results"
                :key="staffmember.login.uuid"
                :staff="staffmember"
            />
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
            errored: false,
            staffmembers: [],
            
        }
    },
     mounted () {
     axios
        .get('https://randomuser.me/api/?results=2')
        .then(response => { 
            this.staffmembers = response.data
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


