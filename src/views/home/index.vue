<template>
  <custom-header
    @create-account="handleAccountCreate"
    @login="handleLogin"
  />
  <contact />
  <div class="flex justify-center py-10 bg-brand-gray">
    <p class="font-medium text-center text-gray-800">feedbacker © 2021</p>
  </div>
</template>

<script>
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'
import CustomHeader from './customHeader.vue'
import Contact from './contact.vue'
import eventBus from '../../utils/bus.js'
export default {
  components: { CustomHeader, Contact },
  setup () {
    const router = useRouter()
    onMounted(() => {
      const token = window.localStorage.getItem('token')
      if (token) {
        router.push({ name: 'Feedbacks' })
      }
    })
    function handleLogin () {
      eventBus.emit('modal:toggle', {
        status: true,
        component: 'ModalLogin'
      })
    }
    function handleAccountCreate () {
      eventBus.emit('modal:toggle', {
        status: true,
        component: 'ModalAccountCreate'
      })
    }
    return {
      handleLogin,
      handleAccountCreate
    }
  }
}
</script>
