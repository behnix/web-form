<template>
  <SignupForm />
</template>

<script>
import SignupForm from './components/SignupForm.vue'

export default {
  name: 'App',
  components: {
    SignupForm
  }
}
</script>

<style>
#app {
  font-family: IRANSans;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body{
  font-family: IRANSans;
  font-size: 20px;
  direction: rtl;
  margin: 0;
  background: #eee;
}
</style>
