<template>
    <div >
          <b-card
          :title="staff.login.username"
          :img-src="staff.picture.large"
          img-alt="Genre Music"
          img-top
          tag="article"
        >
          <b-card-text>
            {{staff.login.username}}
          </b-card-text>
          </b-card>
    </div>
</template>

<script>
    export default {
        props: ['staff'],
    }
</script>

<style scoped>
   
</style>