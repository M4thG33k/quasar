<template>
  <div class="q-layout-padding">
    <q-toggle v-model="horizontal" label="Horizontal" />
    <q-toggle v-model="customStyle" label="Custom style" />
    <q-checkbox v-model="alwaysVisible" toggle-indeterminate label="Always visible" />

    <div style="height: 300px;" />

    <q-scroll-area
      ref="scroll"
      style="width: 400px; height: 500px;"
      class="bg-yellow"
      :horizontal="horizontal"
      :visible="alwaysVisible"
      :bar-style="customStyle === true ? customBarStyle : void 0"
      :thumb-style="customStyle === true ? customThumbStyle : void 0"
    >
      <div :class="{ 'flex no-wrap' : horizontal }">
        <div style="margin-top: 150px" />
        <div style="margin-bottom: 25px" :style="horizontal ? 'width: 160px' : ''" v-for="n in number" :key="n">
          {{ n }} Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
          <q-btn label="Click" color="primary" />
        </div>
      </div>
    </q-scroll-area>

    <q-scroll-area
      ref="scroll"
      style="width: 400px; height: 500px;"
      class="bg-dark text-white q-mt-lg"
      :horizontal="horizontal"
      :visible="alwaysVisible"
      dark
    >
      <div :class="{ 'flex no-wrap' : horizontal }">
        <div style="margin-top: 150px" />
        <div style="margin-bottom: 25px" :style="horizontal ? 'width: 160px' : ''" v-for="n in number" :key="n">
          {{ n }} Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
          <q-btn label="Click" color="primary" />
        </div>
      </div>
    </q-scroll-area>

    <br>
    <q-btn @click="number--">
      Less
    </q-btn>
    <q-btn @click="number++">
      More
    </q-btn>
    <q-btn @click="scroll">
      Scroll to 125
    </q-btn>
    <q-btn @click="scroll2">
      Scroll to 525 (animated)
    </q-btn>

    <div style="height: 1000px" />
  </div>
</template>

<script>
export default {
  data () {
    return {
      number: 10,
      horizontal: false,
      alwaysVisible: true,
      customStyle: true
    }
  },

  computed: {
    customBarStyle () {
      return {
        background: '#666',
        borderStyle: 'solid',
        borderColor: 'transparent',
        borderWidth: this.horizontal === true ? '6px 0' : '0 6px',
        backgroundClip: 'content-box',
        [this.horizontal === true ? 'height' : 'width']: '16px'
      }
    },

    customThumbStyle () {
      return {
        background: '#000',
        borderRadius: '4px',
        borderStyle: 'solid',
        borderColor: 'transparent',
        borderWidth: this.horizontal === true ? '2px 0' : '0 2px',
        backgroundClip: 'content-box',
        [this.horizontal === true ? 'height' : 'width']: '16px'
      }
    }
  },

  methods: {
    scroll () {
      this.$refs.scroll.setScrollPosition(125)
    },
    scroll2 () {
      this.$refs.scroll.setScrollPosition(525, 1000)
    }
  }
}
</script>
