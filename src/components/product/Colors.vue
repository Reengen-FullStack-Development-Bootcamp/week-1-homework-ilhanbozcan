<template>
  
    <div class="colors">
      <div
        @click="selectColor(img)"
        v-for="img in images"
        :key="'img' + img.id"
        class="color"
        :style="{ backgroundColor: img.color }"
      ></div>
    </div>
</template>

<script>
export default {
    name:"Images",
    props:{
        images : Array,
        defaultColor : Number,
        selectColor:Function

    }

}
</script>

<style scoped>
.colors {
  display: grid;
  color: #95afc0;
  grid-template-columns: repeat(auto-fill, 30px);
  width: 60%;
  grid-gap: 4px;
  margin-left: 20px;
  margin-top: 5px;
}
.colors:hover {
  cursor: pointer;
}
.pick {
  margin-top: 11px;
  margin-bottom: 0;
  margin-left: 20px;
}
.color {
  padding: 9px;
  border: 1px solid #95afc0;
  font-size: 0.7em;
  text-align: center;
}
.color:hover {
  background: #95afc0;
  color: #f5f5f5;
  transition: all 0.4s ease-in-out;
}
.focus {
  background: #95afc0;
  color: #f5f5f5;
}
</style>