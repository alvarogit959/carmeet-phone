<template>
  <div class="phone-frame">
    <div class="phone-content">
      <MainView />
    </div>
  </div>
</template>

<script>
import 'leaflet/dist/leaflet.css';
import MainView from "./components/main.vue";

export default {
  name: "App",
  components: {
    MainView,
  },
  data() {
    return {};
  },
  methods: {
    closeWindow() {
      window.electron?.ipcRenderer.send("close-window");
    },
    minimizeWindow() {
      window.electron?.ipcRenderer.send("minimize-window");
    },
    toggleMaximize() {
      window.electron?.ipcRenderer.send("toggle-maximize");
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100;300;400;500;600;700;800;900&display=swap");

* {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
  -webkit-text-size-adjust: 100%;
  letter-spacing: -0.2px;
  line-height: 1.5;
}

html,
body {
overflow: hidden;
height: 100vh;
  width: 100vw;
  
  padding: 0;
  margin: 0;
  background: transparent;
  overflow-x: hidden;
  -webkit-app-region: no-drag;
}

#app {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  font-family: 'Inter', sans-serif;
  text-align: center;
  background: linear-gradient(135deg, rgba(10, 10, 20, 1), rgba(20, 20, 40, 1));
  -webkit-app-region: no-drag;
}

.phone-frame {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  background: linear-gradient(135deg, rgba(10, 10, 20, 1), rgba(20, 20, 40, 1));
}

.phone-content {
  flex: 1;
  overflow-y: auto;
  overflow-x: hidden;
  -webkit-overflow-scrolling: hidden;

}
.phone-content::-webkit-scrollbar {
  width: 0px;
}



.defaultbutton {
  font-family: 'Inter', sans-serif;
  width: 2rem;
  height: 2rem;
  margin: 0.1rem;
  cursor: pointer;
  transition: all 0.25s ease;
  background: rgba(20, 20, 40, 0);

  border: 1px solid rgba(0, 0, 0, 0);
  font-size: 1rem;
  color: white;
}

.defaultbutton:hover {
  background: rgba(168, 85, 247, 0.3);
  transform: translateY(-2px);
}

.defaultbutton:active {
  transform: translateY(0);
}
.main-content,
.view-container,
.chat-panel,
.chat-conversation,
.chat-messages {
  min-height: 0;
}

</style>