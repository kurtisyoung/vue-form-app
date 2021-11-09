<template>
  <div class="thank-you flex flex-column">
    <img src="/assets/icon-sent.png" alt="Sent">
    <h4>Thank you for applying to become a seller with Creative Market!</h4>
    <p>
      Our curators are reviewing your application. We’ll get back to you within <span style="font-weight: 600;">5-7 business days</span>. Meanwhile, you already have access to your Shop Studio, so let’s start setting up your shop!
    </p>
  </div>
</template>

<style lang="scss" scoped>
.thank-you {
  text-align: center;
  justify-content: center;
  align-items: center;
  padding: 75px 20px;
  @media only screen and (min-width: 768px) {
    padding-bottom: 130px;
  }
}
img {
  height: 126px;
  width: 140px;
}
h4 {
  max-width: 400px;
  width: 100%;
  margin: 20px 0 30px;
}
p {
  text-align: center;
  max-width: 520px;
  width: 100%;
}
</style>