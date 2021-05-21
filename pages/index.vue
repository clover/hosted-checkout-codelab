<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        Hosted Checkout Sample
      </h1>
      <div class="links">
        <a
          href="https://docs.clover.com/docs/hosted-checkout-api"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          Documentation
        </a>
        <checkout />
      </div>
    <div>
    </div>
    </div>
  </div>
</template>

<script>
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: Graphik, Helvetica, Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
