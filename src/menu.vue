<template>
    <div class="menu">
        <white_menu v-for="작명 in 메뉴들" :key="작명"> {{ 작명 }} </white_menu>
    </div>

</template>

<script>
export default {
    name: "Menu",
    data() {
        return {
            메뉴들: ['Home', 'Shop', 'About'],
        }
    }
}
</script>

<style>
.menu {
    background: rgb(166, 154, 230);
    padding: 15px;
    border-radius: 5px;
}

.menu white_menu {
    color: white;
    padding: 10px;
}
</style>