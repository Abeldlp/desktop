<template>
  <div>
      <div>
        <button @click="openWindow" style="margin: 20px">Open new window</button>
      </div>
      <window-component v-for="window in openedApps" :key="window.id"></window-component>

  </div>
</template>

<script>
import WindowComponent from "@/components/WindowComponent";
import Linux from "./assets/1228033.png"
export default {
  name: "App",
  data(){
    return {
      backgroundImage : Linux,
      openedApps: [],
    }
  },
  components: {
    WindowComponent
  },
  methods:{
    openWindow(){
      this.openedApps.push({id: Math.floor(Math.random()) * 100})
    }
  }
};
</script>


<style>
body {
  height: 100vh;
  width: 100vw;
  margin: 0;
  padding: 0;
  overflow: auto;
  /*background-image: url("./assets/1228033.png");*/
}


#block1 {
  border: solid black 1px;
  height: 300px;
  width: 300px;
  display: inline-block;
  float: left;
}



.table-block {
  display: table;
}

.table-row {
  display: table-row;
  text-align: center;
}

.table-cell {
  width: 50%;
  display: inline-block;
}

.table-input {
  width: 50px;
}


.table-container {
  flex: 1;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>