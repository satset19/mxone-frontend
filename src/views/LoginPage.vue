<script>
import { mapActions } from "pinia";
import { useCounterStore } from "../stores/counter";
import { RouterLink } from "vue-router";
export default {
  name: "Login",
  data() {
    return {
      input: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    ...mapActions(useCounterStore, ["login"]),
  },
};
</script>

<template>
  <div
    class="bg-[url('https://cdn.mos.cms.futurecdn.net/N6JgmjQCK9NYzwdXBrHSjh.jpg')]"
  >
    <div
      class="min-h-screen flex flex-col items-center justify-center bg-gray-900 bg-opacity-70"
    >
      <div
        class="flex flex-col shadow-md px-4 sm:px-6 md:px-8 lg:px-10 py-8 rounded-3xl w-100 max-w-md bg-black bg-opacity-80"
      >
        <div class="font-medium self-center text-xl sm:text-3xl text-stone-600">
          Login Now
        </div>
        <div class="mt-4 self-center text-xl sm:text-sm text-stone-600">
          Enter your credentials account
        </div>

        <div class="mt-10">
          <form action="#" @submit.prevent="login(input)">
            <div class="flex flex-col mb-5">
              <label
                for="email"
                class="mb-1 text-xs tracking-wide text-gray-600"
                >E-Mail Address:</label
              >
              <div class="relative">
                <div
                  class="inline-flex items-center justify-center absolute left-0 top-0 h-full w-10 text-gray-400"
                >
                  <i class="fas fa-at text-blue-500"></i>
                </div>

                <input
                  v-model="input.email"
                  type="email"
                  class="text-sm placeholder-gray-500 pl-10 pr-4 rounded-2xl border border-gray-400 w-full py-2 focus:outline-none focus:border-blue-400"
                  placeholder="Enter your email"
                />
              </div>
            </div>
            <div class="flex flex-col mb-6">
              <label
                for="password"
                class="mb-1 text-xs sm:text-sm tracking-wide text-gray-600"
                >Password:</label
              >
              <div class="relative">
                <div
                  class="inline-flex items-center justify-center absolute left-0 top-0 h-full w-10 text-gray-400"
                >
                  <span>
                    <i class="fas fa-lock text-blue-500"></i>
                  </span>
                </div>

                <input
                  v-model="input.password"
                  type="password"
                  class="text-sm placeholder-gray-500 pl-10 pr-4 rounded-2xl border border-gray-400 w-full py-2 focus:outline-none focus:border-blue-400"
                  placeholder="Enter your password"
                />
              </div>
            </div>

            <div class="flex w-full">
              <button
                type="submit"
                class="flex mt-2 items-center justify-center focus:outline-none text-white text-sm sm:text-base bg-blue-500 hover:bg-blue-600 rounded-2xl py-2 w-full transition duration-150 ease-in"
              >
                <span class="mr-2 uppercase">Sign in</span>
                <span>
                  <svg
                    class="h-6 w-6"
                    fill="none"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  >
                    <path
                      d="M13 9l3 3m0 0l-3 3m3-3H8m13 0a9 9 0 11-18 0 9 9 0 0118 0z"
                    />
                  </svg>
                </span>
              </button>
            </div>
          </form>
        </div>
      </div>
      <div class="flex justify-center items-center mt-6">
        <!-- <p>{{ this.$route.path }}</p> -->
        <span
          class="ml-2 inline-flex items-center font-medium text-xs text-center text-stone-200"
          >Didn't have an account?
          <RouterLink :to="'/register'">
            <a href="#" class="text-xs ml-2 text-blue-500 font-semibold"
              >Register here</a
            ></RouterLink
          ></span
        >
      </div>
    </div>
  </div>
</template>

<style></style>
