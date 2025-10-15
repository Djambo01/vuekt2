<template>
  <div class="app">
    <nav class="navbar">
      <div class="nav-links">
        <router-link to="/" class="nav-link">Home</router-link>
        <router-link to="/users" class="nav-link">Users</router-link>
        <router-link to="/profile" class="nav-link">Profile</router-link>
      </div>
    </nav>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Heebo', sans-serif;
  background-color: #fff;
}

.app {
  min-height: 100vh;
}

.navbar {
  padding: 16px 32px;
  background-color: #fff;
}

.nav-links {
  display: flex;
  justify-content: flex-end;
  gap: 32px;
  max-width: 1200px;
  margin: 0 auto;
}

.nav-link {
  color: #000;
  text-decoration: none;
  font-size: 20px;
  font-weight: 500;
  padding: 8px;
  transition: color 0.3s;
  font-family: 'Heebo', sans-serif;
}

.nav-link:hover,
.nav-link.router-link-active {
  color: #FF6464;
}
</style> 