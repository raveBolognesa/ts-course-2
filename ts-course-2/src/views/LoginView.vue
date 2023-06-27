<script lang="ts">
import { defineComponent } from 'vue'

enum EnumErrorType {
  WARNING = 'warning',
  DANGER = 'danger',
}
interface Errors {
  message: string
  type: EnumErrorType
}

class ErrorCustom extends Error implements Errors {
  type: EnumErrorType;
  constructor(
      message: string,
      type: EnumErrorType
  ) {
    super();
    this.message = message
    this.type = type
  }

}

interface MyData {
  mail: string
  password: string
  emailRegex: RegExp
  passwordRegex: RegExp
  errors: ErrorCustom[]
}
export default defineComponent({
  data(): MyData {
    return {
      mail: "",
      password: "",
      emailRegex: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
      passwordRegex: /^(?=.*[A-Za-z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!%*#?&]{10,}$/,
      errors: [],
    }
  },
})
</script>

<template>
  <div class="login">

      <h1>Registrate en mi app</h1>
      <form>
        <label>Mail</label><input v-model="mail">
        <label>Password</label><input v-model="password">
        <button type="submit">Registrarse</button>
      </form>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
