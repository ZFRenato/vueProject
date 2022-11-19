<template>
  <modalFactory/>
  <router-view/>
</template>
<script>
import modalFactory from '../src/components/modalFactory'

export default {
  components: { modalFactory }
}
</script>
