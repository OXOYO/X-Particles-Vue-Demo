<style>
  html {
    height: 100%;
    width: 100%;
    padding: 0;
    margin: 0;
  }
  body {
    height: 100%;
    width: 100%;
    font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    padding: 0;
    margin: 0;
  }
  .layout {
    text-align: center;
  }
  .particles-background {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: -1;
    background: #383838;
    height: 100%;
    width: 100%;
  }
  .btn {
    display: inline-block;
    font-weight: 400;
    text-align: center;
    vertical-align: middle;
    touch-action: manipulation;
    cursor: pointer;
    background-image: none;
    border: 1px solid transparent;
    white-space: nowrap;
    line-height: 1.5;
    user-select: none;
    padding: 6px 15px;
    font-size: 12px;
    border-radius: 4px;
    transition: color .2s linear,background-color .2s linear,border .2s linear,box-shadow .2s linear;
    color: #495060;
    background-color: #f7f7f7;
    border-color: #dddee1;
    margin: 0 5px;
  }
  .btn-ghost {
    color: #fff;
    background-color: transparent;
    border-color: #dddee1;
  }
  .btn-ghost:hover {
    color: #57a3f3;
    background-color: transparent;
    border-color: #57a3f3;
  }
  .btn-active {
    color: #fff;
    background-color: #57c5f7;
    border-color: #57c5f7;
  }
</style>

<template>
  <div id="app" class="layout">
    <a href="https://github.com/OXOYO/X-Particles-Vue" target="_blank">
      <img
        style="position: absolute; top: 0; right: 0; border: 0;"
        src="https://s3.amazonaws.com/github/ribbons/forkme_right_orange_ff7600.png"
        alt="Fork me on GitHub"
      >
    </a>
    <img src="./assets/logo.png" style="width: 200px; height: 200px;">
    <h1 style="color: #fff;">X-Particles-Vue</h1>
    <div :class="{'btn': true, 'btn-ghost': true, 'btn-active': 'default' === currentConfig}" @click="switchConfig('default')">default</div>
    <div :class="{'btn': true, 'btn-ghost': true, 'btn-active': 'nasa' === currentConfig}" @click="switchConfig('nasa')">nasa</div>
    <div :class="{'btn': true, 'btn-ghost': true, 'btn-active': 'bubble' === currentConfig}" @click="switchConfig('bubble')">bubble</div>
    <div :class="{'btn': true, 'btn-ghost': true, 'btn-active': 'snow' === currentConfig}" @click="switchConfig('snow')">snow</div>

    <x-particles class="particles-background" :config="config[currentConfig]" v-if="isShow"></x-particles>
  </div>
</template>

<script>
import defConfig from './config/default.js'
import nasaConfig from './config/nasa.js'
import bubbleConfig from './config/bubble.js'
import snowConfig from './config/snow.js'

export default {
  name: 'app',
  components: {},
  data () {
    return {
      config: {
        default: defConfig,
        nasa: nasaConfig,
        bubble: bubbleConfig,
        snow: snowConfig
      },
      currentConfig: 'default',
      isShow: true
    }
  },
  methods: {
    switchConfig: function (type) {
      let _t = this
      _t.isShow = false
      _t.$nextTick(function () {
        _t.currentConfig = type || 'default'
        _t.isShow = true
      })
    }
  }
}
</script>
