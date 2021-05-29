<template>
  <MongoAdminRequest msg="Mongo Admin Request App" />
</template>

<script>
import MongoAdminRequest from './components/MongoAdminRequest.vue'

export default {
  name: 'App',
  components: {
    MongoAdminRequest: MongoAdminRequest
  }
}
</script>
