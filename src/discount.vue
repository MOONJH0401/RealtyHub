<template>

  <div  v-if="discountPercentage > 0" class="discount">
    <h4>지금 결제하면 {{ discountPercentage }}% 할인</h4>

  </div>


</template>

<script>
export default {
  name: 'Discount',
  data() {
    return {
      discountPercentage: 20 // 초기 할인율 설정
    };

  },
  mounted() {
    // 1초마다 할인율을 1%씩 감소시키는 타이머 설정
    setInterval(this.decrementDiscount, 1000);
  },
  methods: {
    decrementDiscount() {
      if (this.discountPercentage > 0) {
        this.discountPercentage--; // 할인율을 1%씩 감소
      } else {
        clearInterval(this.intervalId); // 할인율이 0이 되면 타이머 정지
      }
    }
  }
};


</script>

<style>
.discount {
  width: 300px;
  background-color: rgb(141, 199, 199);
  border-radius: 15px;
  padding: 5px;
  display: block;
  margin-left: auto;
  margin-right: auto;
  font-size: 15px;
  box-shadow: 5px 5px black;
}
</style>