<template>
<div>
<b-container fluid >
    <b-container fluid>
        <Carrousel />
    </b-container>   
</b-container>

</div>
  
</template>

<script>

export default {
    data () {
        return {
            header: 'Top 5 Music Events in WA'
        }
    }

}
</script>

<style scoped>
.header {
        font-weight: 700;
        font-size: 1.5rem;
        margin-left: 1.5rem;
    }

   
   
</style>