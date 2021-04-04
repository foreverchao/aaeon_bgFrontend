<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <router-view></router-view>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import 'bootstrap/dist/css/bootstrap.min.css'
import GlobalHeader , { UserProps }  from '../components/GlobalHeader.vue'

const currentUser: UserProps = {
    isLogin: true,
    name: 'Yue',
}
export default defineComponent({
  name: 'Home',
  components: {
    GlobalHeader
  },
  setup() {
    return {
      currentUser
    }
  }
});
</script>
