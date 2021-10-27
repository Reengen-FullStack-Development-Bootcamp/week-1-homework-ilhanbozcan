<template>
  <select v-model="quantity" class="select-dropdown mx-2">
            <option v-for="s in size" :key='s' :value='s'>{{s}}</option>
            
          </select>
</template>

<script>
export default {
    name : "QuantitySelect",
    props:{
        size : Number
    },
    data() {
        return {
            quantity: 1,
        };
    },
    watch:{
        quantity(val){
            this.$emit('update-quantity',val)
        }
    }
}
</script>

<style scoped>

.select-dropdown,
.select-dropdown * {
  margin: 0;
  padding: 0;
  height: 35px;
  position: relative;
  box-sizing: border-box;
}
.select-dropdown {
  position: relative;
  background-color: #f5f5f5;
  border-radius: 4px;
}


</style>