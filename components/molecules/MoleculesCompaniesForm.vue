<template>
  <form class="w-full card" @submit.prevent="createCompany">
    <AtomsInputText type="email" label-text="Name" v-model="company.name" />
    <AtomsInputText type="Logo" label-text="Name" v-model="company.logo" />
    <IamgeUploader label="Logo" />
    <AtomsButton
      button-type="submit"
      text="Sign In"
      class="w-full btn btn-primary mt-[14px]"
    />
  </form>
</template>

<script>
import AtomsInputText from '~/components/atoms/AtomsInputText'
import AtomsButton from '~/components/atoms/AtomsButton'
import IamgeUploader from '~/components/molecules/ImageUploader'
export default {
  name: 'MoleculesCompaniesForm',
  components: { IamgeUploader, AtomsButton, AtomsInputText },
  data(){
    return{
      previewImage: null,
      company: {
        name: '',
        logo: null,
      },
    }
  },
  methods:{
    async createCompany() {
      try {
        const formData = new FormData()
        formData.append('name', this.company.name)
        formData.append('logo', this.company.logo)
        let create = this.$axios
          .post('/company', formData)
          .then((response) => {
            this.$router.push({
              name: 'companies-id',
              params: {
                id: response.data.result.id,
              },
            })
          })
      } catch (err) {}
    },
  }
}
</script>

<style scoped></style>
