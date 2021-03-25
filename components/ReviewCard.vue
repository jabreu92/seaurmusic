<template>
  <div class="review-card">
    <div class="image-container">
      <img :src="reviewpic" alt="" />
    </div>
    <div class="text-container">
      <h6>{{reviewusername}}</h6>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Repellendus
        quam magni beatae possimus debitis.
      </p>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        reviewusername: {
            type: String,
            required: true,
            default: "Random UserName goes here" // Pass in the specific parameters instead of teh whole objet , best practice
        },
        reviewpic: {
            type: String,
            required: true,
            default: "https://picsum.photos/200/300" // Pass in the specific parameters instead of teh whole objet , best practice
        }

    }
}
</script>

<style scoped>
.review-card {
  margin-top: 1.5rem;
  height: 4rem;
  display: flex;
}
.text-container {
  margin-left: 2rem;
}
img {
  width: 4rem;
  height: 4rem;
  border-radius: 100%;
}
p {
  color: grey;
}
</style>
