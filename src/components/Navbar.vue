<script>
import { mapActions, mapState } from "pinia";
import { RouterLink } from "vue-router";
import { useCounterStore } from "../stores/counter";
export default {
  name: "Navbar",
  computed: {
    ...mapState(useCounterStore, ["carts"]),
  },
  methods: {
    ...mapActions(useCounterStore, ["logout", "fetchCart"]),
  },
  created() {
    this.fetchCart();
  },
};
</script>

<template>
  <div class="flex justify-between navbar bg-black rounded-lg">
    <div class="dropdown dropdown-bottom">
      <label tabindex="0" class="btn btn-ghost btn-circle avatar">
        <div class="w-10 rounded-full">
          <img
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSjoHrB31r1oNOm7rV1t5qDVihasO7N6gPNCg&s"
          />
        </div>
      </label>
      <ul
        tabindex="0"
        class="menu menu-compact dropdown-content mt-3 p-2 shadow bg-black rounded-box w-52"
      >
        <li>
          <a class="justify-between">
            Profile
            <span class="badge">New</span>
          </a>
        </li>
        <li><a>Settings</a></li>
        <li @click.prevent="logout"><a>Logout</a></li>
      </ul>
    </div>
    <div class="flex items-center justify-center">
      <RouterLink :to="'/'"
        ><a class="btn btn-ghost normal-case text-xl text-slate-50"
          >MXOne</a
        ></RouterLink
      >
    </div>
    <div class="dropdown dropdown-end">
      <label tabindex="0" class="btn btn-ghost btn-circle">
        <div class="indicator">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"
            />
          </svg>
          <span class="badge badge-sm indicator-item">{{ carts.length }}</span>
        </div>
      </label>
      <div
        tabindex="0"
        class="mt-3 card card-compact dropdown-content w-52 bg-base-100 shadow"
      >
        <div class="card-body bg-black">
          <span class="font-bold text-lg">{{ carts.length }} Items</span>
          <span class="text-info">Subtotal: Rp. 198,982,392.00</span>
          <h1 v-for="cart in carts">{{ cart.Movie.title }}</h1>
          <RouterLink :to="'/cart'">
            <div class="card-actions">
              <button class="btn btn-primary btn-block">View cart</button>
            </div>
          </RouterLink>
        </div>
      </div>
    </div>
  </div>
</template>
