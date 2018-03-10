<template>
</template>

<script>
  import L from 'leaflet'

  export default {
    // Expects ids as one or more WMS layer IDs (comma-separated)
    props: ['baseurl', 'format', 'transparent', 'ids', 'crs', 'opacity'],
    mounted () {
      this.$tileLayer = L.tileLayer.wms(this.baseurl, {
        format: this.format,
        transparent: this.transparent,
        layers: this.ids,
        crs: this.crs,
        opacity: this.opacity
      })
    },
    methods: {
      deferredMountedTo (parent) {
        this.$tileLayer.addTo(parent);
      }
    }
  }
</script>
