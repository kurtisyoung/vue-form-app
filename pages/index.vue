<template>
  <div class="vue-form-app relative flex items-top justify-center min-h-screen md:items-center md:pt-0">
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.1.2/dist/tailwind.min.css" rel="stylesheet">
    <Header />
    <div class="form-card max-w-4xl mx-auto md:px-6 lg:px-8 bg-white overflow-hidden">
      <div v-if="!submitted" class="p-6">
        <h3 class="sub-title">Seller Application</h3>
        <Form />
      </div>
      <ThankYou v-if="submitted" />
    </div>
    <BgPattern />
  </div>
</template>

<script>
export default {
  data() {
    return {
      submitted: false
    }
  }
}
</script>

<style lang="scss">
body {
  font-family: Helvetica, Arial !important;
  color: #303538 !important;
}
.vue-form-app {
  position: relative;
  h4 {
    font-size: 24px;
    font-style: normal;
    font-weight: 600;
    line-height: 34px;
    letter-spacing: 0px; 
  }
  p {
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 22px;
    letter-spacing: 0px;
  }
}
.form-card {
  position: relative;
  margin-top: 6.1rem;
  width: 100%;
  @media only screen and (min-width: 768px) {
    margin-top: 6rem;
    box-shadow: 0px 2px 10px rgba(226, 233, 238, 0.6);
    border-radius: 8px;
  }
}
.sub-title {
  font-weight: 600;
  font-size: 12px;
  line-height: 12px;
  letter-spacing: 0.25px;
  text-transform: uppercase;
  margin-bottom: 8px;
}

</style>