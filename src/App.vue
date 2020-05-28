<template>
  <div id="app">
    <transition name="fade">
      <ul v-if="isVisibled" class="cards">
        <li v-for="person in people" :key="person.name" class="card">
          <p class="name">
            {{ person.name }}
          </p>
          <p class="age">
            {{ person.age }}
          </p>
          <p class="job">
            {{ person.job }}
          </p>
        </li>
      </ul>
    </transition>

    <button ref="hoge" type="button" @click="onClick">
      実行
    </button>

    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <h1>BAU-YA</h1>
    <p>はじめてのVue.js</p>
    <router-view />
  </div>
</template>

<script>
export default {
  data() {
    return {
      isVisibled: true,
      people: [
        {
          name: "沖 良矢",
          age: 38,
          job: "Web制作"
        },
        {
          name: "長州 力",
          age: 69,
          job: "元プロレスラー"
        },
        {
          name: "アントニオ猪木",
          age: 77,
          job: "元国会議員"
        }
      ]
    };
  },
  methods: {
    onClick() {
      this.isVisibled = !this.isVisibled;
    }
  }
};
</script>

<style lang="scss" scoped>
.fade-enter-active {
  transition: opacity 1s ease;
}

.fade-enter {
  opacity: 0;
}

.cards {
  display: flex;
  justify-content: center;
}

.card {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin-right: 10px;
  width: 280px;
  height: 380px;
  background-color: green;
  color: white;
  border-radius: 8px;
  opacity: 0.9;
}

.name {
  font-size: 20px;
  font-weight: bold;
}

.age {
  font-size: 12px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
