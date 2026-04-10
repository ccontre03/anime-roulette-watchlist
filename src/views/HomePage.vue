<script setup>
import { reactive, ref } from 'vue'

const accountCreated = ref(false)

const createAccountForm = reactive({
  firstName: 'John',
  lastName: 'Doe',
  email: 'john@example.com',
  address: '123 Main St, City, State',
  password: 'password123',
  favoriteFood: 'Margherita Pizza',
})

const favoriteSpots = ref([
  {
    id: 1,
    name: "Tony's Pizza Palace",
    category: 'Italian',
  },
  {
    id: 2,
    name: 'Sushi Paradise',
    category: 'Japanese',
  },
  {
    id: 3,
    name: 'Taco Fiesta',
    category: 'Mexican',
  },
  {
    id: 4,
    name: 'Burger Corner',
    category: 'American',
  },
])

const createAccount = () => {
  accountCreated.value = true
}

const resetTemplate = () => {
  accountCreated.value = false
}
</script>

<template>
  <main class="min-h-screen bg-[var(--page-bg)] text-slate-900">
    <header class="border-b border-orange-100 bg-white/90">
      <div class="mx-auto flex max-w-6xl items-center justify-between px-6 py-4 lg:px-10">
        <div class="flex items-center gap-3">
          <div class="flex h-11 w-11 items-center justify-center rounded-2xl bg-orange-100 text-xl">
            🍽️
          </div>
          <div>
            <p class="text-2xl font-semibold tracking-tight">Local Foodie</p>
            <p class="text-sm text-slate-500">Simple account template</p>
          </div>
        </div>

        <button
          v-if="accountCreated"
          type="button"
          class="rounded-full border border-orange-200 px-5 py-2 text-sm font-medium text-orange-600 transition hover:bg-orange-50"
          @click="resetTemplate"
        >
          Back to Create Account
        </button>
      </div>
    </header>

    <div class="mx-auto max-w-6xl px-6 py-12 lg:px-10">
      <section
        v-if="!accountCreated"
        class="mx-auto max-w-2xl"
      >
        <div class="mb-8 text-center">
          <div class="mx-auto mb-4 flex h-18 w-18 items-center justify-center rounded-[28px] bg-gradient-to-br from-orange-400 to-amber-300 text-4xl shadow-[0_18px_40px_rgba(249,115,22,0.2)]">
            🍽️
          </div>
          <h1 class="text-4xl font-semibold tracking-tight sm:text-5xl">Create Account</h1>
          <p class="mt-3 text-lg text-slate-600">Sign up to start discovering local food</p>
        </div>

        <section class="template-card p-6 sm:p-8">
          <div class="grid gap-4 sm:grid-cols-2">
            <label class="template-field">
              <span>First Name</span>
              <input
                v-model="createAccountForm.firstName"
                type="text"
                class="template-input"
              />
            </label>

            <label class="template-field">
              <span>Last Name</span>
              <input
                v-model="createAccountForm.lastName"
                type="text"
                class="template-input"
              />
            </label>
          </div>

          <div class="mt-4 space-y-4">
            <label class="template-field">
              <span>Email</span>
              <input
                v-model="createAccountForm.email"
                type="email"
                class="template-input"
              />
            </label>

            <label class="template-field">
              <span>Address</span>
              <input
                v-model="createAccountForm.address"
                type="text"
                class="template-input"
              />
            </label>

            <label class="template-field">
              <span>Password</span>
              <input
                v-model="createAccountForm.password"
                type="password"
                class="template-input"
              />
            </label>

            <label class="template-field sm:col-span-2">
              <span>Favorite Food</span>
              <input
                v-model="createAccountForm.favoriteFood"
                type="text"
                class="template-input"
              />
            </label>
          </div>

          <button
            type="button"
            class="template-button mt-6"
            @click="createAccount"
          >
            Create Account
          </button>
        </section>
      </section>

      <section
        v-else
        class="space-y-8"
      >
        <div class="flex flex-col gap-5 rounded-[32px] bg-white p-6 shadow-[0_18px_50px_rgba(15,23,42,0.08)] sm:flex-row sm:items-center sm:justify-between sm:p-8">
          <div class="flex items-center gap-4">
            <div class="flex h-20 w-20 items-center justify-center rounded-full bg-orange-100 text-2xl font-semibold text-orange-600">
              {{ createAccountForm.firstName.charAt(0) }}{{ createAccountForm.lastName.charAt(0) }}
            </div>
            <div>
              <p class="text-sm font-medium uppercase tracking-[0.25em] text-orange-500">
                Account Created
              </p>
              <h1 class="mt-2 text-4xl font-semibold tracking-tight">
                {{ createAccountForm.firstName }} {{ createAccountForm.lastName }}
              </h1>
              <p class="mt-2 text-lg text-slate-600">
                Favorite food: {{ createAccountForm.favoriteFood }}
              </p>
            </div>
          </div>

          <p class="max-w-sm text-sm text-slate-500 sm:text-right">
            This can be the starting screen for a signed-in user profile.
          </p>
        </div>

        <div class="grid gap-6 lg:grid-cols-[1.1fr_0.9fr]">
          <section class="template-card p-6 sm:p-8">
            <h2 class="text-2xl font-semibold">Profile Details</h2>
            <div class="mt-6 grid gap-4 sm:grid-cols-2">
              <div class="rounded-2xl bg-[var(--panel-soft)] p-4">
                <p class="text-sm text-slate-500">First Name</p>
                <p class="mt-2 text-lg font-medium">{{ createAccountForm.firstName }}</p>
              </div>

              <div class="rounded-2xl bg-[var(--panel-soft)] p-4">
                <p class="text-sm text-slate-500">Last Name</p>
                <p class="mt-2 text-lg font-medium">{{ createAccountForm.lastName }}</p>
              </div>

              <div class="rounded-2xl bg-[var(--panel-soft)] p-4">
                <p class="text-sm text-slate-500">Email</p>
                <p class="mt-2 text-lg font-medium">{{ createAccountForm.email }}</p>
              </div>

              <div class="rounded-2xl bg-[var(--panel-soft)] p-4">
                <p class="text-sm text-slate-500">Address</p>
                <p class="mt-2 text-lg font-medium">{{ createAccountForm.address }}</p>
              </div>
            </div>
          </section>

          <section class="template-card p-6 sm:p-8">
            <h2 class="text-2xl font-semibold">Visited Restaurants</h2>
            <div class="mt-6 flex flex-col items-center">
              <div class="wheel-frame">
                <div class="visit-wheel">
                  <div class="wheel-center">4 Visits</div>
                </div>
              </div>

              <div class="mt-6 grid w-full gap-3">
                <article
                  v-for="spot in favoriteSpots"
                  :key="spot.id"
                  class="flex items-center justify-between rounded-2xl bg-[var(--panel-soft)] px-4 py-3"
                >
                  <div>
                    <p class="text-base font-medium">{{ spot.name }}</p>
                    <p class="mt-1 text-sm text-slate-500">{{ spot.category }}</p>
                  </div>
                  <span class="text-sm font-medium text-orange-500">Visited</span>
                </article>
              </div>
            </div>
          </section>
        </div>
      </section>
    </div>
  </main>
</template>
