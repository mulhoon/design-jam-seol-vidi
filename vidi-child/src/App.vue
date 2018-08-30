<template>
  <device>
    <div id="app" :class="{active:active, broadcasting:broadcasting}">
      <div class="header">
        Chatting with mum
      </div>
        <div class='video girl'  @click="broadcast">
          <div class='status'>LIVE</div>
        </div>
        <div class='video mum'></div>
        <div class='controls'>
          <div class="button" @click="goLive" v-if="!broadcasting"></div>
          <div class="button live" @click="end" v-else></div>
        </div>
      </div>
    </device>
</template>

<script>
import device from 'vue-device'

export default {
  name: 'app',
  components: {
    device,
  },
  data() {
    return {
      active: false,
      broadcasting: false,
    }
  },
  methods: {
    goLive() {
      this.active = true
      this.broadcasting = false
    },
    broadcast() {
      this.active = false
      this.broadcasting = true
    },
    end() {
      this.active = false
      this.broadcasting = false
    },
  },
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
  background: #0074d9;
  color: #2c3e50;
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
.video {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: #ccc;
  border-radius: 4px;
  transition: all 0.3s ease-in-out;
  background-size: 100%;
  overflow: hidden;
  &.girl {
    background-image: url('./assets/video.png');
  }
  &.mum {
    background-image: url('./assets/mum.png');
    transform: translate3d(120%, 0, 0) scale(1);
    box-shadow: 0 40px 40px rgba(#000, 0.3);
  }
}
.status {
  background: red;
  color: #fff;
  display: block;
  position: absolute;
  top: 20px;
  right: 20px;
  border-radius: 4px;
  padding: 5px 15px;
  font-weight: 700;
  box-shadow: 0 0 20px rgba(#000, 0.5);
  transition: all 0.3s ease-in-out;
  transform: translate3d(0, 0, 0) scale(0);
}
#app.active {
  .girl {
    transform: translate3d(-40%, 0, 0) scale(0.6);
    filter: brightness(0.5);
  }
  .mum {
    transform: translate3d(25%, 0, 0) scale(0.8);
  }
  .controls {
    transform: translate3d(0, 140%, 0) scale(1);
  }
}
#app.broadcasting {
  .status {
    transition-delay: 0.3s;
    transform: translate3d(0, 0, 0) scale(1);
  }
}
.controls {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 100px;
  width: 100%;
  z-index: 10;
  transition: all 0.3s ease-in-out;
  .button {
    width: 60px;
    height: 60px;
    text-align: center;
    border-radius: 50px;
    line-height: 60px;
    margin: auto;
    background: red;
    color: #fff;
    font-weight: bold;
    font-size: 1.2em;
    cursor: pointer;
    position: relative;
    margin-top: -17px;
    &:after {
      position: absolute;
      left: -7px;
      top: -7px;
      width: 66px;
      height: 66px;
      content: '';
      border: 4px solid #fff;
      display: block;
      border-radius: 100px;
    }
    &.live {
      border-radius: 4px;
      width: 40px;
      height: 40px;
      background: red;
      margin-top: -7px;
      &:after {
        left: -17px;
        top: -17px;
      }
    }
  }
}
</style>
