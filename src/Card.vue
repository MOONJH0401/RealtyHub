<template>
  <div class='room'>
    <div>
      <img :src="room.image" class="room-img" />
   
      <h4 @click="$emit('open_modal', room.id)"> {{ room['title'] }} </h4>
      <h4 @click="$emit('open_modal', room.id)"> {{ room['price'] }} 원 </h4>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    room: Object,
    모달창정보: Object,
  }
}
</script>

<style></style>