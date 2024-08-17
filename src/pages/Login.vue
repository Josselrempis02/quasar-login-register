<template>
  <div class="fixed-center q-pa-xl border-2 border-rounded">
    <div class="login-form">
      <h1 class="text-h3 text-center">Login</h1>
      <form>
        <div class="q-pa-s" style="max-width: 300px">
          <q-input
            filled
            v-model="text"
            label="Email"
            style="width: 100%;" 
          />
        </div>
        <div class="form-group" style="max-width: 300px;">
          <q-input
            filled
            v-model="text1"
            label="Password"
            style="width: 100%;" 
          />
        </div>
        <button type="submit">Login</button>
      </form>
    </div>
  </div>
</template>

  
<script setup>
import { ref } from 'vue'

defineOptions({
  name: 'UserLogin'
});

const text = ref('')
</script>

  
  <style>
  .border-rounded {
  border-color: black;
  border-style:  solid;
  border-radius: 10px;
}


  
  
  </style>
  