<template>
  <div>
    <h3 class="my-5">스테디 셀러 | <span style="font-size: 70%">꾸준히 잘 팔리는 상품</span></h3>
    <v-sheet class="mx-auto" flat outlined rounded>
      <v-slide-group class="pa-2" show-arrows>
        <SteadySellerCard v-for="(steadySeller, idx) in steadySellerList" :steadySeller="steadySeller" :key="idx" />
      </v-slide-group>
    </v-sheet>
    <div class="loadingDiv">
      <spinner :loading="loding"></spinner>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex';
import Spinner from '../Spinner.vue';
import SteadySellerCard from './SteadySellerCard.vue';

export default {
  name: 'SteadySeller',
  components: {
    SteadySellerCard,
    Spinner,
  },
  computed: {
    ...mapState('mainStore', ['steadySellerList','loding']),
  },
};
</script>
