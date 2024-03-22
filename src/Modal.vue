<template>
  <div v-if="모달창정보['is_open'] == true" class="black-bg">
    <div class="white-bg">
      <h2> {{ 원룸들[모달창정보.room_id].title }} </h2>
      <p> {{ 원룸들[모달창정보.room_id].content }}</p>
      <p> 월 {{ 원룸들[모달창정보.room_id].price }} 원</p>
      <p> 중개수수료 {{ fee }}원</p>
      <input v-model.number="month">개월
      <input v-model="month" type="range" min="1" max="12">
      <h1>{{ month }}개월 선택 : 총 {{ 원룸들[모달창정보.room_id].price * month + fee }}원 </h1>
      <button @click="increase(원룸들[모달창정보.room_id])">허위매물신고</button>
      <span> 신고수 : {{ 원룸들[모달창정보.room_id].신고수 }}</span>
      <p></p>
      <a :href="원룸들[모달창정보.room_id].주소">
        <button class="botton_style"> 결제하기 </button>
      </a>
      <button @click="$emit('close_modal'); month = default_month" class="botton_style"> 나가기 </button>
      <p>조회수</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  data() {
    return {
      default_month: 3,
      month: this.default_month,
      fee: 100000
    }
  },

  watch: {
    month(newValue) {
      const isKorean = /[ㄱ-ㅎㅏ-ㅣ가-힣]/.test(newValue);
      if (newValue > 12) {
        alert('13 이상은 불가능합니다.');
        this.month = this.default_month;
      }
      if (isKorean) {
        alert('한글은 사용할 수 없습니다.');
        this.month = this.default_month;
      }
    }
  },

  updated() {
    this.checkMonth();
  },

  props: {
    원룸들: Array,
    모달창정보: Object,
  },

  methods: {
    increase(원룸) {
      원룸.신고수 += 1;
      this.checkMonth();
    },
    checkMonth() {
      if (this.month < 3) {
        console.log(this.month)
        alert('3개월 이상을 선택해주세요!');
      }
    }
  }
}
</script>

<style>
.black-bg {
  display: flex;
  align-items: center;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.432);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background-color: white;
  padding: 20px;
  border-radius: 8px;
}

.botton_style {
  margin: 0 15px 0 0;
  display: inline-block;
  border-radius: 5px;
  background: #38988d;
  font-size: 15px;
}
</style>