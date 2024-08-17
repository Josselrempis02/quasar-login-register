<template>
    <div class="fixed-center q-pa-xl border-rounded full-width" style="max-width: 500px;">
      <div class="login-form">
        <h1 class="text-h3 text-center">Sign In</h1>
        <form>
          <div class="q-gutter-md row ">
            <div class="col-6">
              <q-input
                filled
                v-model="fullName"
                label="Full Name"
                class="q-mb-md"
                color="orange-7"
              />
            </div>
            <div class="col-5">
              <q-input
                filled
                v-model="username"
                label="Username"
                class="q-mb-md"
                color="orange-7"
              />
            </div>
          </div>
  
          <q-input
            filled
            v-model="email"
            label="Email Address"
            class="q-mb-md"
            color="orange-7"
          />
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
  
          <q-btn 
            color="primary"
            label="Sign Up"
            class="full-width "
          />
        </form>
        
        <div class="text-center q-mt-md">
          <span>Already have an account?</span>
          <q-btn 
            flat
            color="primary"
            label="Sign In"
            @click="goToSignIn"
          />
        </div>
      </div>
    </div>
  </template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

defineOptions({
    name: 'UserSignup'
  });

const fullName = ref('');
const username = ref('');
const email = ref('');
const password = ref('');
const showPassword = ref(false);

const router = useRouter();

const goToSignIn = () => {
  router.push('/login');
};
</script>

<style>
.border-rounded {
  border-color: black;
  border-style: solid;
  border-radius: 10px;
}
</style>


  