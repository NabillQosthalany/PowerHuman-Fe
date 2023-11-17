<template>
  <div class="form-group">
    <label for="" class="text-grey">{{ label }}</label>
    <input
      type="file"
      @change="uploadImage"
      ref="fileInput"
      class="hidden"
    />
    <div
      class="relative border-2 border-dashed border-gray-400 rounded-lg p-8 flex items-center justify-center"
    >
      <div v-if="!previewImage">
        <span class="text-gray-600">Upload An Image</span>
      </div>
      <img
        v-else
        :src="previewImage"
        alt="preview"
        class="w-32 h-32 object-cover rounded-lg"
      />
      <button
        type="button"
        @click="triggerFileInput"
        class="absolute inset-0 w-full h-full bg-transparent cursor-pointer"
      ></button>
    </div>
  </div>
</template>

<script>
export default {
  name: "IamgeUploader",
  data(){
    return{
      previewImage: null,
    }
  },
  props:{
    label:{
    label:{
      type:String,
      required:true
    }
    }
  },
  methods:{
    triggerFileInput() {
      this.$refs.fileInput.click()
    },
    uploadImage(event) {
      const file = event.target.files[0]
      if (file && file.type.includes('image')) {
        const reader = new FileReader()
        reader.onload = () => {
          this.previewImage = reader.result
        }
        reader.readAsDataURL(file)
        this.team.logo = file
      } else {
        this.previewImage = null
        this.team.logo = null
      }
    },
  }
}
</script>

<style scoped>

</style>
