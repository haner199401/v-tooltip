<template>
  <div class="page-home page">

    <section class="nav">
      <router-link
        :to="{ name: 'install' }"
        v-tooltip="{
          content: 'Installation Instruction page',
          delay: { show: 400, hide: 0 },
        }"
      >
        Get Started
      </router-link>
      <a href="https://github.com/Akryum/v-tooltip#usage">Documentation</a>
      <a href="https://github.com/Akryum/v-tooltip/issues">Report an issue</a>
    </section>

    <section class="demo">
      <div class="section-content">
        <h2>Reactive content</h2>
        <input class="tooltip-content" v-model="msg" placeholder="Tooltip content" />

        <button class="tooltip-target" v-tooltip.top-center="msg">Hover me</button>
      </div>
    </section>

    <section class="snippets">
      <Collapse title="Show code">
        <div class="section-content">
          <CodeSnippet class="snippet" :code="mainSnippet" lang="js"/>
          <div class="plus">+</div>
          <CodeSnippet class="snippet" :code="componentSnippet1" lang="html"/>
          <div class="plus">+</div>
          <CodeSnippet class="snippet" :code="styleSnippet1" lang="scss"/>
        </div>
      </Collapse>
    </section>

    <section class="demo">
      <div class="section-content">
        <h2>Customize it!</h2>
        <button class="tooltip-target b2" v-tooltip="{
          content: 'You can change a lot of parameters: placement, classes, offset, delay...',
          placement: 'bottom-center',
          classes: ['info'],
          offset: 100,
          delay: {
            show: 500,
            hide: 0,
          },
        }">Hover me</button>
      </div>
    </section>

    <section class="snippets">
      <Collapse title="Show code">
        <div class="section-content">
          <CodeSnippet class="snippet" :code="componentSnippet2" lang="html"/>
          <div class="plus">+</div>
          <CodeSnippet class="snippet" :code="styleSnippet2" lang="scss"/>
        </div>
      </Collapse>
    </section>

  </div>
</template>

<script>
import CodeSnippet from './CodeSnippet.vue'
import Collapse from './Collapse.vue'

const mainSnippet = `
import Vue from 'vue'
import VTooltip from 'v-tooltip'

Vue.use(VTooltip)

new Vue({
  data: {
    msg: 'This is a button.'
  }
})
`

const componentSnippet1 = `
<button v-tooltip.top-center="msg">Hover me</button>
`

const styleSnippet1 = `
.tooltip {
  display: block !important;
  z-index: 10000;

  .tooltip-inner {
    background: black;
    color: white;
    border-radius: 16px;
    padding: 5px 10px 4px;
  }

  .tooltip-arrow {
    width: 0;
    height: 0;
    border-style: solid;
    position: absolute;
    margin: 5px;
    border-color: black;
  }

  &[x-placement^="top"] {
    margin-bottom: 5px;

    .tooltip-arrow {
      border-width: 5px 5px 0 5px;
      border-left-color: transparent !important;
      border-right-color: transparent !important;
      border-bottom-color: transparent !important;
      bottom: -5px;
      left: calc(50% - 5px);
      margin-top: 0;
      margin-bottom: 0;
    }
  }

  &[x-placement^="bottom"] {
    margin-top: 5px;

    .tooltip-arrow {
      border-width: 0 5px 5px 5px;
      border-left-color: transparent !important;
      border-right-color: transparent !important;
      border-top-color: transparent !important;
      top: -5px;
      left: calc(50% - 5px);
      margin-top: 0;
      margin-bottom: 0;
    }
  }

  &[x-placement^="right"] {
    margin-left: 5px;

    .tooltip-arrow {
      border-width: 5px 5px 5px 0;
      border-left-color: transparent !important;
      border-top-color: transparent !important;
      border-bottom-color: transparent !important;
      left: -5px;
      top: calc(50% - 5px);
      margin-left: 0;
      margin-right: 0;
    }
  }

  &[x-placement^="left"] {
    margin-right: 5px;

    .tooltip-arrow {
      border-width: 5px 0 5px 5px;
      border-top-color: transparent !important;
      border-right-color: transparent !important;
      border-bottom-color: transparent !important;
      right: -5px;
      top: calc(50% - 5px);
      margin-left: 0;
      margin-right: 0;
    }
  }

  &[aria-hidden='true'] {
    visibility: hidden;
    opacity: 0;
    transition: opacity .15s, visibility .15s;
  }

  &[aria-hidden='false'] {
    visibility: visible;
    opacity: 1;
    transition: opacity .15s;
  }
}
`

const componentSnippet2 = `
<button v-tooltip="{
  content: msg,
  placement: 'bottom-center',
  classes: ['info'],
  offset: 100,
  delay: {
    show: 500,
    hide: 0,
  },
}">Hover me</button>`

const styleSnippet2 = `
.tooltip {
  &.info {
    $color: rgba(#004499, .9);

    .tooltip-inner {
      background: $color;
      color: white;
      padding: 24px;
      border-radius: 5px;
      box-shadow: 0 5px 30px rgba(black, .1);
    }

    .tooltip-arrow {
      border-color: $color;
    }
  }
}
`

export default {
  name: 'Home',
  components: {
    CodeSnippet,
    Collapse,
  },
  data () {
    return {
      msg: `This is a button.`,
      mainSnippet,
      componentSnippet1,
      styleSnippet1,
      componentSnippet2,
      styleSnippet2,
    }
  },
}
</script>