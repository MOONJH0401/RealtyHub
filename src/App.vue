<template>
  
    <Transition name="modalfade">
      <Modal @close_modal="모달창정보.is_open = false" :원룸들="원룸들" :모달창정보="모달창정보" />
    </Transition>

 

          <Menu />


          <Discount />

        
        <div>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
              정렬
            </a>
            <ul class="dropdown-menu">
              <li> <button @click="priceSort()" class="dropdown-item" href="#">최저가순</button></li>
              <li> <button @click="priceSort1()" class="dropdown-item" href="#">최고가순</button></li>
              <li> <button @click="sortBack()" class="dropdown-item" href="#">되돌리기</button></li>
            </ul>
          </li>

        </div>
      





  <Card @open_modal="모달창정보.is_open = true; 모달창정보.room_id = $event" :모달창정보="모달창정보" :room="room" v-for="room in 원룸들"
    :key="room" />

</template>

<script>
import data from './assets/room.js';
import Discount from './discount.vue';
import Menu from './menu.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'App',
  data() {
    return {
      
      원룸들오리지날: [...data],
      모달창정보: { is_open: false, room_id: null },
      원룸들: data,
    }
  },
  methods: {
    increase(원룸) {
      원룸.신고수 += 1;
    },
    priceSort() {
      this.원룸들.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    priceSort1() { // 오타 수정: priceSort1 메서드의 위치와 이름 수정
      this.원룸들.sort(function (a, b) {
        return b.price - a.price;
      });
    },
    sortBack() {
      this.원룸들 = [...this.원룸들오리지날];
    }
  },



  components: {
    Discount: Discount,
    Menu: Menu,
    Modal: Modal,
    Card: Card,
  },
}
</script>

<style>
.modalfade-enter-from {
  opacity: 0;
}

.modalfade-enter-active {
  transition: all 1s;
}

.modalfade-enter-to {
  opacity: 1;
}

body {
  margin: 0
}

div {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000407;

}
</style>
