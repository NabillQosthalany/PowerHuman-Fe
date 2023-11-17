<template>
  <section class="py-[50px] flex flex-col items-center justify-center px-4">
    <img src="/assets/svgs/logo-type.svg" alt="" />
    <div class="text-[32px] font-semibold text-dark mt-[70px]">Sign In</div>
    <p class="mt-4 text-base leading-7 text-center mb-[50px] text-grey">
      Manage your employees to achieve <br />
      a bigger goals for your company
    </p>
    <MoleculesLoginForm/>
  </section>
</template>
<script>
import MoleculesLoginForm from "~/components/molecules/MoleculesLoginForm";
export default {
  components: {MoleculesLoginForm},
  auth: 'local',
}
</script>
