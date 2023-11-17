<template>
  <section class="py-[200px] flex flex-col items-center justify-center px-4">
    <div class="text-[32px] font-semibold text-dark mb-4">Select Companies</div>
    <MoleculesCompaniesForm/>
  </section>
</template>

<script>
import MoleculesCompaniesForm from "~/components/molecules/MoleculesCompaniesForm";
export default {
  components: {MoleculesCompaniesForm},

  middleware: 'auth',
}
</script>

<style></style>
