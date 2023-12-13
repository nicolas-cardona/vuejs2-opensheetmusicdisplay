<template>
  <div class="open-sheet-music-display-component">
    <div ref="container"></div>
  </div>
</template>

<script>
import { OpenSheetMusicDisplay as OSMD } from 'opensheetmusicdisplay'

export default {
  name: 'OsmdComponent',

  data() {
    return {
      osmd: null,
    };
  },

  props: {
    file: {
      type: String,
      required: true,
    },
    autoResize: {
      type: Boolean,
      required: false,
      default: true,
    },
  },

  mounted() {
    this.setupOsmd()
  },

  methods: {
    async setupOsmd() {
      if (this.$refs.container) {
        this.osmd = new OSMD(this.$refs.container, { autoResize: this.autoResize });
        await this.osmd.load(this.file, this.title);
        await this.osmd.render();
      }
    },
  },
};
</script>

<style lang="sass" scoped>

.sheet-music-component

</style>
