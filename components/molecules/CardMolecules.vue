<template>
  <div class="card !gap-y-10 min-h-[200px]">
    <div class="flex items-center justify-between">
      <div>
        <p class="text-grey">{{ cardText }}</p>
        <div class="text-[32px] font-bold text-dark mt-[6px]">{{cardValue}}</div>
      </div>
      <NuxtLink :to="linkTo"
      ><img src="/assets/svgs/ric-plus.svg" alt=""
      /></NuxtLink>
    </div>
  </div>

</template>

<script>
export default {
  name: "CardMolecules",
  props:{
    cardText:{
      type:String,
      required:true
    },
    cardValue:{
      type:String,
      required:true
    },
    linkTo:Object
  }
}
</script>

<style scoped>

</style>
