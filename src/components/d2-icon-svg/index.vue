<template>
  <svg aria-hidden="true" style="height: 21px;width:21px">
    <use :xlink:href="icon"></use>
  </svg>
</template>

<script>
export default {
  name: 'd2-icon-svg',
  props: {
    name: {
      type: String,
      required: true
    }
  },
  computed: {
    icon () {
      return `#${this.name}`
    }
  }
}
</script>
