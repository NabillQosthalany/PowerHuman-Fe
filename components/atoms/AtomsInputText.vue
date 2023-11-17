<template>
  <div class="form-group">
    <label for="" class="text-grey">{{ labelText }}</label>
    <input
      :value="internalValue"
      :type="type"
      class="input-field"
      @input="updateValue"
    />
  </div>
</template>

<script>
export default {
  name: 'AtomsInputText',
  data() {
    return {
      internalValue: this.value,
    }
  },
  props: {
    labelText: {
      type: String,
      required: true,
    },
    value: {
      type: String,
    },
    type:{
      type:String,
      required:true
    }
  },
  methods: {
    updateValue(event) {
      this.internalValue = event.target.value
      this.$emit('input', this.internalValue)
    },
  },
}
</script>

<style scoped></style>
