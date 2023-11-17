<script>
import AtomsInputText from '~/components/atoms/AtomsInputText'
import AtomsButton from '~/components/atoms/AtomsButton'
export default {
  name: 'MoleculesLoginForm',
  components: { AtomsButton, AtomsInputText },
  data() {
    return {
      login: {
        email: '',
        password: '',
      },
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    },
  },
}
</script>
<template>
  <form class="w-full card" @submit.prevent="userLogin">
    <AtomsInputText
      type="email"
      label-text="Username"
      v-model="login.email"
    />
    <AtomsInputText
      type="password"
      label-text="Password"
      v-model="login.password"
    />
    <AtomsButton
      button-type="submit"
      text="Sign In"
      class="w-full btn btn-primary mt-[14px]"
    />
  </form>
</template>
