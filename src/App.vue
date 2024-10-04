<template>
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
    crossorigin="anonymous"
  />
  <div>
    <center>
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
          <router-link class="navbar-brand" to="/">VUE SPA</router-link>
          <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#navbarNav"
            aria-controls="navbarNav"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
              <li class="nav-item">
                <router-link class="nav-link" to="/">Home</router-link>
              </li>
              <li class="nav-item">
                <router-link class="nav-link" to="/about">About</router-link>
              </li>
              <li class="nav-item">
                <router-link class="nav-link" to="/to-do-list"
                  >To Do List</router-link
                >
              </li>
            </ul>
          </div>
        </div>
      </nav>
      <router-view></router-view>
    </center>
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
.navbar {
  justify-content: center;
}
</style>
