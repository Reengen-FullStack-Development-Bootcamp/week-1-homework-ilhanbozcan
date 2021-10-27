<template>
<div>
   <p class="pick">choose size</p>
    <div class="sizes">
      <div
        @click="selectSize(size)"
        v-for="size in sizes"
        :key="'size-' + size.id"
        :class="['size', { focus: defaultSize === size.id }]"
      >
        {{ size.name }}
      </div>
    </div>
    </div>
</template>

<script>
export default {
    name:"Sizes",
    props:{
        sizes : Array,
        defaultSize : Number,
        selectSize : Function
    }
}
</script>

<style scoped>

p {
  font-size: 0.6em;
  color: #95afc0;
  letter-spacing: 1px;
}

.sizes {
  display: grid;
  color: #95afc0;
  grid-template-columns: repeat(auto-fill, 30px);
  width: 60%;
  grid-gap: 4px;
  margin-left: 20px;
  margin-top: 5px;
}
.sizes:hover {
  cursor: pointer;
}
.pick {
  margin-top: 11px;
  margin-bottom: 0;
  margin-left: 20px;
}
.size {
  padding: 9px;
  border: 1px solid #95afc0;
  font-size: 0.7em;
  text-align: center;
}
.size:hover {
  background: #95afc0;
  color: #f5f5f5;
  transition: all 0.4s ease-in-out;
}
.focus {
  background: #95afc0;
  color: #f5f5f5;
}
</style>