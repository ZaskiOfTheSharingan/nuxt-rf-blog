<template>
  <div>
    <header class="blog-header py-3">
      <div
        class="d-flex flex-row justify-content-between px-4 nav-underline border border-top-0 py-2 align-content-center"
      >
        <NuxtLink class="h1" to="/">Blog</NuxtLink>
      </div>
    </header>
    <main>
      <Nuxt />
    </main>
    <footer class="footer bg-gradient justify-items-center">
      <p class="footer-text">Created by Denis Zaoral</p>
    </footer>
  </div>
</template>

<style>
main {
  padding: 0px 100px 0px 100px;
}

.h1 {
  text-decoration: none;
}

.footer {
  text-align-last: center;
  align-content: center;
  height: 90px;
  padding-top: 35px;
  margin-top: 40px;
  background: #dbdbdb;
  border-radius: 5px 5px 0px 0px;
  -moz-border-radius: 5px 5px 0px 0px;
  -webkit-border-radius: 5px 5px 0px 0px;
  border: 0px solid #000000;
  -webkit-box-shadow: 0px -6px 50px -16px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 0px -6px 50px -16px rgba(0, 0, 0, 0.75);
  box-shadow: 0px -6px 50px -16px rgba(0, 0, 0, 0.75);
}

.footer-text {
  padding: 0;
  margin-top: 0px;
}
</style>
