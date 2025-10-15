<template>
  <div class="login-page">
    <div class="login-container">
      <form @submit.prevent="handleLogin" class="login-form">
        <h1>Authorization</h1>
        <div class="form-group">
          <label for="login">Login</label>
          <input
            type="text"
            id="login"
            v-model="username"
            required
            class="form-input"
          >
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input
            type="password"
            id="password"
            v-model="password"
            required
            class="form-input"
          >
        </div>
        <div v-if="error" class="error-message">
          {{ error }}
        </div>
        <button type="submit" class="submit-button">Submit</button>
      </form>
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
  name: 'LoginView',
  data() {
    return {
      username: '',
      password: '',
      error: '',
      isLoading: false
    }
  },
  methods: {
    async handleLogin() {
      try {
        this.error = ''
        this.isLoading = true

        if (!this.username.trim() || !this.password.trim()) {
          throw new Error('Пожалуйста, заполните все поля')
        }

        const response = await fetch('https://dummyjson.com/auth/login', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            username: this.username,
            password: this.password,
          }),
        })

        const data = await response.json()

        if (!response.ok) {
          throw new Error(data.message || 'Ошибка авторизации')
        }

        // Сохраняем accessToken в localStorage
        localStorage.setItem('token', data.accessToken)
        localStorage.setItem('user', JSON.stringify(data))

        // Перенаправляем на страницу профиля
        this.$router.push('/profile')
        
      } catch (error) {
        this.error = error.message || 'Произошла ошибка при авторизации'
      } finally {
        this.isLoading = false
      }
    }
  }
}
</script>

<style scoped>
.login-page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  font-family: 'Heebo', sans-serif;
}

.login-container {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 32px;
}

h1 {
  font-size: 34px;
  font-weight: 700;
  color: #21243D;
  margin-bottom: 40px;
}

.login-form {
  width: 100%;
  max-width: 400px;
  background: #FFFFFF;
  border-radius: 20px;
  padding: 32px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.25);
}

.form-group {
  margin-bottom: 24px;
}

label {
  display: block;
  font-size: 16px;
  color: #21243D;
  margin-bottom: 8px;
}

.form-input {
  width: 100%;
  height: 47px;
  padding: 0 16px;
  border: none;
  border-radius: 20px;
  font-size: 16px;
  color: #21243D;
  transition: border-color 0.3s;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.25);
}

.form-input:focus {
  outline: none;
}

.submit-button {
  width: 100%;
  height: 47px;
  background: #ff646400;
  border: none;
  border-radius: 4px;
  color: rgb(91, 91, 91);
  font-size: 20px;
  font-weight: 500;
  cursor: pointer;
  transition: background-color 0.3s;
}

.submit-button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.error-message {
  color: #FF6464;
  margin-bottom: 16px;
  font-size: 14px;
}

.footer {
  text-align: center;
  padding: 32px 0;
}

.social-links {
  margin-bottom: 16px;
}

.social-link {
  color: #21243D;
  font-size: 24px;
  margin: 0 8px;
  text-decoration: none;
  transition: color 0.3s;
}

.social-link:hover {
  color: #FF6464;
}

.copyright {
  color: #8695A4;
  font-size: 14px;
  margin: 0;
  font-weight: 400;
}
</style>