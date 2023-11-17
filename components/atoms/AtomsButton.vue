<template>
  <button  @click="eventClick" :type="buttonType" id="continueBtn">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'AtomsButton',
  props: {
    text: {
      type: String,
      required: true,
    },
    buttonType:{
      type: String,
      default:'Button'
    }
  },
  methods: {
    eventClick() {
      this.$emit('eventClick')
    },
  },
}
</script>

<style scoped></style>
