<template>
  <section class="py-[50px] flex flex-col items-center justify-center px-4">
    <img src="/assets/svgs/logo-type.svg" alt="">
    <div class="text-[32px] font-semibold text-dark mt-[70px]">
      Sign Up
    </div>
    <p class="mt-4 text-base leading-7 text-center mb-[50px] text-grey">
      Manage your employees to achieve <br> a bigger goals for your company
    </p>
   <MoleculesRegisterForm/>
  </section>
</template>

<script>
import MoleculesRegisterForm from "~/components/molecules/MoleculesRegisterForm";
export default {
  components: {MoleculesRegisterForm},
  auth:'guest',
}
</script>
