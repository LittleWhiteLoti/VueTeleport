<template>
    <header>
        <h1> {{ Title }} </h1>
    </header>
</template>

<script>
export default {

    props: {
        title: {
            type: String,
            required: true
        }
    },
    data() {
        return {
            Title: this.$props.title
        }
    }
}

</script>

<style scoped>

header {
  width: 100%;
  height: 5rem;
  background-color: #640032;
  display: flex;
  justify-content: center;
  align-items: center;
}

h1 {
  color: white;
  margin: 0;
}

</style>