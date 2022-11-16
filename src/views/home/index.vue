<template>
  <customHeader
    @create-acount="handlerAcountCreat"
    @login="handlerLogin"
  />
  <contact/>
  <div class="flex justify-center py-10 bg-brand-gray">
    <p class="font-medium text-center text-gray-800">feedbacker &copy; 2022</p>
  </div>
</template>
<script>
import { onMounted } from '@vue/runtime-core'
import { useRouter } from 'vue-router'
import customHeader from './customHeader.vue'
import contact from './contact.vue'

export default {
  components: { customHeader, contact },

  setup () {
    const router = useRouter()
    onMounted(() => {
      const token = window.localStorage.getItem('token')
      if (token) {
        router.push({ name: 'Feedback' })
      }
    })

    function handlerLogin () { }
    function handlerAcountCreate () { }

    return {
      handlerLogin,
      handlerAcountCreate
    }
  }
}
</script>
