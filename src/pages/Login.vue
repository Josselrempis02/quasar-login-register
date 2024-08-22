<template>
  <div
    class="fixed-center q-pa-xl border-rounded full-width"
    style="max-width: 500px"
  >
    <div class="login-form">
      <h1 class="text-h3 text-center">Login</h1>
      <form>
        <div class="q-pa-s">
          <q-input
            filled
            v-model="email"
            label="Email Address"
            class="q-mb-md"
            color="orange-7"
          />
        </div>
        <div class="q-pa-s">
          <q-input
            filled
            v-model="password"
            label="Password"
            type="password"
            class="q-mb-sm"
            color="orange-7"
          />
          <q-checkbox
            v-model="showPassword"
            label="Show Password"
            class="q-mb-sm"
            color="orange-7"
          />
        </div>
        <q-btn color="primary" label="Login" class="full-width custom-hover" />
      </form>

      <div class="text-center q-mt-md">
        <span>Don't have an account?</span>
        <q-btn flat color="primary" label="Sign up" @click="goToSignUp" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

defineOptions({
  name: "UserLogin",
});

const email = ref("");
const password = ref("");
const showPassword = ref(false);

const router = useRouter();

// Navigate to signup page
const goToSignUp = () => {
  router.push("/signup");
};
</script>

<style>
.border-rounded {
  border-color: black;
  border-style: solid;
  border-radius: 10px;
}

.custom-hover:hover {
  background-color: #1565c0; /* Darker primary color for hover effect */
  color: white;
}
</style>
