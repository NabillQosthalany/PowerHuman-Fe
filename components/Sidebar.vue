<template>
  <div>
    <div
      class="hidden lg:block fixed lg:max-w-[295px] w-full overflow-y-auto h-full bg-white z-[999]"
      id="sidebarHRIS"
    >
      <div class="px-6 py-[50px] gap-y-[50px] flex flex-col">
        <div class="flex items-center justify-between">
          <a href="#" class="flex justify-center">
            <img src="/assets/svgs/logo-type.svg" alt="" />
          </a>
          <a href="#" id="toggleCloseSidebar" class="lg:hidden">
            <svg
              class="w-6 h-6 text-dark"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M6 18L18 6M6 6l12 12"
              ></path>
            </svg>
          </a>
        </div>
        <div class="flex flex-col gap-4">
          <div class="text-sm text-grey">Daily Use</div>
          <NuxtLink
            :to="{ name: 'companies-id' }"
            :class="navLinkClasses('companies-id')"
          >
            <img src="/assets/svgs/ic-grid.svg" alt="" />
            Overview
          </NuxtLink>
          <NuxtLink
            :to="{ name: 'companies-id-employees' }"
            :class="navLinkClasses('companies-id-employees')"
          >
            <img src="/assets/svgs/ic-users.svg" alt="" />
            Employees
          </NuxtLink>
          <NuxtLink
            :to="{ name: 'companies-id-teams' }"
            :class="navLinkClasses('companies-id-teams')"
          >
            <img src="/assets/svgs/ic-briefcase.svg" alt="" />
            My Teams
          </NuxtLink>
          <NuxtLink
            :to="{ name: 'companies-id-roles' }"
            :class="navLinkClasses('companies-id-roles')"
          >
            <img src="/assets/svgs/ic-flag.svg" alt="" />
            Roles
          </NuxtLink>
        </div>
        <div class="flex flex-col gap-4">
          <div class="text-sm text-grey">Others</div>
          <a href="#" :class="navLinkClasses('companies-id#')">
            <img src="/assets/svgs/ic-box.svg" alt="" />
            Insurances
          </a>
          <NuxtLink
            :to="{ name: 'companies-id' }"
            :class="navLinkClasses('companies-id#')"
          >
            <img src="/assets/svgs/ic-flag.svg" alt="" />
            Company
          </NuxtLink>
          <a href="#" :class="navLinkClasses('companies-id#')">
            <img src="/assets/svgs/ic-gift.svg" alt="" />
            Rewards
          </a>
          <a href="#" :class="navLinkClasses('companies-id#')">
            <img src="/assets/svgs/ic-settings.svg" alt="" />
            Settings
          </a>
          <button
            @click="$auth.logout()"
            :class="navLinkClasses('companies-id#')"
          >
            <img src="/assets/svgs/ic-signout.svg" alt="" />
            Logout
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Sidebar',
  data() {
    return {
      activePage: null,
    }
  },
  methods: {
    navLinkClasses(routeName) {
      return {
        'nav-link': true,
        'nav-link active': this.$route.name === routeName,
      }
    },
    setActivePage(routeName) {
      this.activePage = routeName
    },
  },
}
</script>

<style scoped></style>
