<template>
  <div id="app">
    <h1>The Dog Database</h1>
    <div id="menu">
      <div id="brand">
        <router-link to="/">
          <img src="/images/logo.png">
        </router-link>
      </div>
    </div>
    <nav>
      <router-link to="/"><button>Home</button></router-link>
      <router-link to="/dashboard"><button>My Dogs</button></router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>

#menu {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "none brand side";
  margin-bottom: 50px;
}

#menu a {
  color: #B84901;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#brand img {
  height: 200px;
}

.menu-item {
  display: flex;
  flex-direction: column;
}

.menu-item p {
  margin: 0px;
}

h1 {
  text-align: center;
}
nav {
  padding: 20px;
  text-align: center;
}
</style>
