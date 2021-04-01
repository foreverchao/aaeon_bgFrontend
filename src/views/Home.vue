<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <div class="home"></div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import 'bootstrap/dist/css/bootstrap.min.css'
import GlobalHeader  from '../components/GlobalHeader.vue'
interface UserProps {
  isLogin: boolean;
  name?: string;
  id?: number;
}
const currentUser: UserProps = {
    isLogin: false,
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
