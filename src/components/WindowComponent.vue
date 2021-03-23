<template>
  <div>
    <vue-resizable
        class="resizable"
        ref="resizableComponent"
        :dragSelector="dragSelector"
        :active="handlers"
        :fit-parent="fit"
        :width="width"
        :height="height"
        :left="left"
        :top="top"
        @mount="eHandler"
        @resize:move="eHandler"
        @resize:start="eHandler"
        @resize:end="eHandler"
        @drag:move="eHandler"
        @drag:start="eHandler"
        @drag:end="eHandler"
    >
      <div class="block">
        <div class="drag-container-1">
          <div @click="closeWindow" class="close_button">X</div>
          <div class="window_name">Window name</div>
        </div>
        <div class="table-container">
          This is a window man
        </div>

      </div>
    </vue-resizable>
  </div>
</template>

<script>
import VueResizable from "vue-resizable";
export default {
  name: "WindowComponent",
  components: { VueResizable },
  data() {
    const tW = 450;
    const tH = 250;
    return {
      handlers: ["r", "rb", "b", "lb", "l", "lt", "t", "rt"],
      left: `calc( 50% - ${tW / 2}px)`,
      top: `calc(50% - ${tH / 2}px)`,
      height: tH,
      width: tW,
      maxW: 250,
      maxH: 250,
      minW: 100,
      minH: 100,
      fit: false,
      event: "",
      dragSelector: ".drag-container-1, .drag-container-2"
    };
  },
  methods: {
    eHandler(data) {
      this.width = data.width;
      this.height = data.height;
      this.left = data.left;
      this.top = data.top;
      this.event = data.eventName;
    },
    closeWindow(e){
      e.target.style.color= "blue"
    }
  },
  filters: {
    checkEmpty(value) {
      return typeof value !== "number" ? 0 : value;
    }
  },

}


</script>

<style scoped>
  .block {
    height: 100%;
    width: 100%;
    background-color: #373737;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 10px;

  }

.resizable {
  width: 350px;
  height: 350px;
  padding: 0;
  font-weight: normal;
  color: black;
  position: absolute;
  border-radius: 10px;
  box-shadow: 1px 12px 36px 8px rgba(0,0,0,0.30);
  -webkit-box-shadow: 1px 12px 36px 8px rgba(0,0,0,0.30);
  -moz-box-shadow: 1px 12px 36px 8px rgba(0,0,0,0.30);
}

.drag-container-1{
  width: 100%;
  height: 30px;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  background: black;
  cursor: pointer;
  display: flex;
  align-content: center;
  justify-content: flex-end;
}
.table-container {
  flex: 1;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.close_button{
  height: 20px;
  width: 20px;
  background-color: #d72d11;
  margin: 5px;
  border-radius: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  color: whitesmoke;
  opacity: 0.9;
}
.window_name{
  position: absolute;

  left: 45%;
  top: 5px;
  overflow: visible;
  color: whitesmoke;
}
</style>