<template>
  <div class="users">
    <div class="users-container">
      <div v-for="user in users" :key="user.id" class="user-card">
        <div class="user-info">
          <div class="user-name">{{ user.firstName }} {{ user.lastName }}</div>
          <div class="user-email">{{ user.email }}</div>
        </div>
      </div>
      <div class="user-card">
        <div class="user-info">
          <div class="user-name">...</div>
        </div>
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
  name: 'UsersView',
  data() {
    return {
      users: []
    }
  },
  async created() {
    try {
      const response = await fetch('https://dummyjson.com/users')
      const data = await response.json()
      this.users = data.users
    } catch (error) {
      console.error('Ошибка при загрузке пользователей:', error)
    }
  }
}
</script>

<style scoped>
.users {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  padding: 32px;
  font-family: 'Heebo', sans-serif;
}

.users-container {
  flex: 1;
  max-width: 800px;
  margin: 0 auto;
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 32px 0;
}

.user-card {
  background: #FFFFFF;
  border-radius: 4px;
  padding: 24px;
  box-shadow: 0px 4px 10px rgba(187, 225, 250, 0.25);
  transition: all 0.3s ease;
}

.user-card:hover {
  box-shadow: 0px 4px 10px rgba(187, 225, 250, 0.4);
  transform: translateY(-2px);
}

.user-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.user-name {
  font-size: 20px;
  font-weight: 500;
  color: #21243D;
}

.user-email {
  font-size: 16px;
  color: #8695A4;
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
  transition: color 0.3s;
}

.social-link:hover {
  color: #FF6464;
}

.copyright {
  color: #21243D;
  font-size: 14px;
  margin: 0;
  font-weight: 400;
}
</style> 