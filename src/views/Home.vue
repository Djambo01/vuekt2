<template>
  <div class="home">
    <div class="content">
      <div class="text-content">
        <h1>Home page</h1>
        <p>
          Amet minim mollit non deserunt ullamco est sit aliqua dolor do amet
          sint. Velit officia consequat duis enim velit mollit. Exercitation veniam
          consequat sunt nostrud amet.
        </p>
        <router-link to="/login" class="auth-button">Authorization</router-link>
      </div>
      <div class="image-content">
        <img src="/tools.svg" alt="Tools" class="tools-image">
      </div>
    </div>
    <footer class="footer">
      <div class="social-links">
        <a href="#" class="social-link"><img src="/fb.svg" alt="Facebook"></a>
        <a href="#" class="social-link"><img src="/insta.svg" alt="Instagram"></a>
        <a href="#" class="social-link"><img src="/tw.svg" alt="Twitter"></a>
        <a href="#" class="social-link"><img src="/lin.svg" alt="Linkedin"></a>
      </div>
      <p class="copyright">Copyright ©2020 All rights reserved</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'HomeView'
}
</script>

<style scoped>
.home {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  padding: 32px;
}

.content {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  max-width: 1200px;
  margin: 0 auto;
  padding: 32px;
  gap: 64px;
}

.text-content {
  flex: 1;
}

.image-content {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

h1 {
  font-size: 44px;
  margin-bottom: 1.5rem;
  color: #21243D;
}

p {
  font-size: 16px;
  line-height: 1.6;
  color: #21243D;
  margin-bottom: 32px;
}

.auth-button {
  display: inline-block;
  width: 208px;
  height: 43px;
  padding: 10px 50px;
  background-color: #FF6464;
  color: white;
  text-decoration: none;
  font-size: 18px;
}


.tools-image {
  width: 300px;
  height: auto;
}

.footer {
  text-align: center;
  padding: 32px 0;
  margin-top: auto;
}

.social-links {
  margin-bottom: 16px;
}

.social-link {
  color: #21243D;
  font-size: 24px;
  margin: 0 8px;
  text-decoration: none;
}

.copyright {
  color: #21243D;
  font-size: 14px;
  margin: 0;
}
</style> 