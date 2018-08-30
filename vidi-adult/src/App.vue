<template>
  <device>
    <div id="app" :class="{active:show}" @click="showIt">
<!--       <div class="header">
        Chatting with mum
      </div> -->
      <div class="cover"></div>
        <div class='video girl'  @click="broadcast">
          <div class='status'>BACK</div>
        </div>
        <div class='video mum'>
          <div class='status'>FRONT</div>
        </div>
        <div class='controls'>
          <!-- <div class="button" @click="goLive" v-if="!broadcasting">BROADCAST</div> -->
          <!-- <div class="button live" @click="goLive" v-else>LIVE</div> -->
        </div>
      </div>
    </device>
</template>

<script>
import device from 'vue-device'

export default {
  name: 'app',
  components: {
    device
  },
  data() {
    return {
      active: false,
      broadcasting: false,
      show: false
    }
  },
  methods: {
    showIt() {
      this.show = !this.show
    },
    goLive() {
      this.active = true
      this.broadcasting
    },
    broadcast() {
      this.active = false
      this.broadcasting = true
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  width: 50%;
  width: 100%;
  height: 100%;
  background: #333;
  color: #2c3e50;
  background-size: 100%;
  background-image: url('./assets/homescreen.png');
  // margin-top: 60px;
}
// .page{
//   width: 50%;
//   position: absolute;
//   top:0;
//   left:0;
//   height:100%;
//   border:1px solid red;
// }
.header {
  color: #fff;
  width: 100%;
  text-align: center;
  padding-top: 20px;
}
.status {
  background: #000;
  color: #fff;
  display: block;
  position: absolute;
  top: 20px;
  right: 20px;
  border-radius: 4px;
  padding: 5px 15px;
  font-weight: 700;
  box-shadow: 0 0 20px rgba(#000, 0.5);
  transition: all 0.5s ease-in-out;
  // transform: translate3d(0, 0, 0) scale(0);
}
.mum .status {
  right: auto;
  left: 20px;
}
.video {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: #ccc;
  border-radius: 4px;
  transition: all 0.5s ease-in-out;
  background-size: 100%;
  box-shadow: 0 40px 40px rgba(#000, 0.3);
  &.girl {
    background-image: url('./assets/video.png');
    transform: translate3d(-120%, -50%, 0) scale(0.2);
  }
  &.mum {
    background-image: url('./assets/girl.png');
    transform: translate3d(120%, 50%, 0) scale(0.2);
  }
}
.cover {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background: rgba(pink, 1);
  opacity: 0;
  transition: all 0.5s ease-in-out;
}
#app.active {
  .girl {
    transform: translate3d(-31%, -12%, 0) scale(0.6);
  }
  .mum {
    transform: translate3d(31%, -12%, 0) scale(0.6);
  }
  .controls {
    transition-delay: 0.2s;
    transform: translate3d(0, 0, 0) scale(1);
  }
  .cover {
    opacity: 1;
  }
}

.controls {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 178px;
  width: 100%;
  z-index: 10;
  transition: all 0.3s ease-in-out;
  background-size: 100%;
  background-image: url('./assets/ui.png');
  background-repeat: no-repeat;
  transform: translate3d(0, 100%, 0) scale(1);
  .button {
    width: 200px;
    height: 60px;

    text-align: center;
    border-radius: 50px;
    line-height: 60px;
    margin: auto;
    background: #666;
    color: #fff;
    font-weight: bold;
    font-size: 1.2em;
    cursor: pointer;
    &.live {
      background: red;
    }
  }
}
</style>
