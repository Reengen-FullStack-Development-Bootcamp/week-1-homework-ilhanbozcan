<template>
  <b-form-rating
        readonly
        v-model="value"
        variant="warning"
        inline
        class="my-2 d-flex justify-content-center"
      ></b-form-rating>
</template>

<script>
export default {
    name: "Stars",
    props: {
        value: Number,
    },
}
</script>

<style>

</style>