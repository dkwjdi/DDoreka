<template>
  <v-slide-item @click.native="moveItemDetail">
    <v-card class="ma-4" height="200" width="200">
      <template slot="progress">
        <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
      </template>
      <v-img :src="`data:image/jpeg;base64,${hotItem.thumbnail}`" height="150" width="200"></v-img>
      <v-card-text class="pa-1 ml-2">
        <div class="mb-1 subtitle-1 font-weight-bold text-truncate" color="black">
          <!-- 상품이름 -->
          {{ hotItem.name }}
        </div>
        <v-row align="center" justify="start" class="mx-0">
          <!-- 평균평점 -->
          <v-rating :value="hotItem.rating" color="warning" background-color="warning lighten-1" dense half-increments readonly size="16"></v-rating>

          <!-- 평균평점, 리뷰개수 -->
          <div class="ml-1">({{ hotItem.review_cnt }})</div>
        </v-row>
      </v-card-text>
    </v-card>
  </v-slide-item>
</template>

<script>
export default {
  name: 'HotItemCard',
  props: {
    hotItem: { type: Object },
  },
  methods: {
    moveItemDetail: function() {
      // 추후 Item Detail페이지 url을 입력
      this.$router.push({ name: 'ItemDetail', params: { id: 1, productid: this.hotItem.productId } });
    },
  },
};
</script>

<style></style>
