<script>
import AtomsInputText from '~/components/atoms/AtomsInputText'
import AtomsButton from '~/components/atoms/AtomsButton'
export default {
  name: 'MoleculesRegisterForm',
  components: { AtomsButton, AtomsInputText },
  data() {
    return {
      register: {
        name: '',
        email: '',
        password: '',
      },
    }
  },
  methods: {
    async userRegister() {
      try {
        //registration data
        let response = await this.$axios.post('/register', this.register)

        //if successfully
        try {
          let response = await this.$auth.loginWith('local', {
            data: {
              email: this.register.email,
              password: this.register.password,
            },
          })
          console.log(login)
        } catch (err) {
          console.log(err)
        }
        console.log(response)
      } catch (err) {
        console.log(err)
      }

      try {
        let response = await this.$auth.loginWith('local', { data: this.register })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    },
  },
}
</script>
<template>
  <form class="w-full card" @submit.prevent="userRegister">
    <AtomsInputText type="text" label-text="Name" v-model="register.name" />
    <AtomsInputText type="email" label-text="Email" v-model="register.email" />
    <AtomsInputText
      type="password"
      label-text="Password"
      v-model="register.password"
    />
    <AtomsButton
      button-type="submit"
      text="Sign In"
      class="w-full btn btn-primary mt-[14px]"
    />
  </form>
</template>
