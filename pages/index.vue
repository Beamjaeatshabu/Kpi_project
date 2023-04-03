<template>
  <div>
    <img :src="imageUrl" alt="My Image">
  </div>
</template>

<script>
export default {
  data() {
    return {
      imageUrl: 'https://images.unsplash.com/photo-1617396900799-f4ec2b43c7ae?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8NHx8d2FsbHBhcGVyJTIwNGt8ZW58MHx8MHx8&w=1000&q=80'
    }
  }
}
</script>
