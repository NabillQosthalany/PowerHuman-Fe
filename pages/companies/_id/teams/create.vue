<template>
  <section class="py-[70px] flex flex-col items-center justify-center px-4">
    <div class="text-[32px] font-semibold text-dark">Build New Team</div>
    <p class="mt-4 text-base leading-7 text-center mb-[50px] text-grey">
      Team that can bring your company <br />
      growing bigger and bigger
    </p>
    <form class="w-full card" @submit.prevent="createTeams">
      <div class="mb-[2px] mx-auto">
        <img src="/assets/svgs/ric-box.svg" alt="" />
      </div>
      <div class="form-group">
        <label for="" class="text-grey">Email Address</label>
        <input
          type="email"
          class="input-field disabled:bg-grey disabled:outline-none"
          :value="this.$auth.user.email"
          disabled
        />
      </div>
      <div class="form-group">
        <label for="" class="text-grey">Team Name</label>
        <input
          v-model="team.name"
          type="text"
          class="input-field"
          value="Growth Marketing"
        />
      </div>
      <div class="form-group">
        <label for="" class="text-grey">Logo</label>
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
      <div class="form-group">
        <label for="" class="text-grey">Status</label>
        <select
          name=""
          id=""
          class="appearance-none input-field form-icon-chevron_down"
        >
          <option value="" selected>Active</option>
          <option value="">Inactive</option>
        </select>
      </div>
      <button type="submit" class="w-full btn btn-primary mt-[14px]">
        Continue
      </button>
    </form>
  </section>
</template>

<script>
export default {
  name: 'create',
  layout: 'form',
  middleware: 'auth',
  data() {
    return {
      previewImage: null,
      team: {
        name: '',
        logo: null,
        company_id: this.$route.params.id,
      },
    }
  },
  methods: {
    triggerFileInput() {
      this.$refs.fileInput.click()
    },
    async createTeams() {
      try {
        const formData = new FormData()
        formData.append('name', this.team.name)
        formData.append('logo', this.team.logo)
        formData.append('company_id', this.team.company_id)
        let create = this.$axios.post('/team', formData).then((response) => {
          this.$router.push({
            name: 'companies-id-teams',
            params: {
              id: response.data.id,
            },
          })
        })
      } catch (err) {}
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
  },
}
</script>

<style scoped></style>
