<template>
    <Modal
        @closeModal="
            isOpen = false;
            clickMove = $event;
        "
        :room="myRoomData"
        :isOpen="isOpen"
        :clickMove="clickMove"
    />

    <div class="menu">
        <a v-for="a in menu" :key="a">{{ a }}</a>
    </div>

    <Discount />

    <Card
        @openModal="
            isOpen = true;
            clickMove = $event;
        "
        :room="myRoomData[i]"
        v-for="(room, i) in myRoomData"
        :key="room"
    />

    <!-- <Card :roomData="roomData" :clickMove="clickMove" :isOpen="isOpen" /> -->
    <!-- 반복분 부분
    <div v-for="(a, i) in products" :key="i" class="menu-detail">
        <h4>{{ a }}</h4>
        <p>{{ price[i] }}만원</p>
    </div> -->
</template>

<script>
var 어레이 = [10, 20, 30];
어레이[0];

function 어쩌구() {
    console.log("콘솔창");
}
어쩌구();

import roomData from "./assets/roomData.js";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
    name: "App",
    // vue 변수 담아두는 방법
    data() {
        return {
            clickMove: 0,
            myRoomData: roomData,
            isOpen: false,
            menu: ["Home", "Shop", "About"],
            products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
            price: [100, 80, 60],
            신고수: [Number(0), Number(0), Number(0)],
        };
    },
    // 함수 선언
    methods: {
        increase() {
            this.신고수++;
        },
    },
    components: { Discount, Modal, Card },
};
</script>

<style>
body {
    margin: 0;
}

div {
    box-sizing: border-box;
}

.black-bg {
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    position: fixed;
    padding: 20px;
}

.white-bg {
    width: 100%;
    background-color: white;
    border-radius: 8px;
    padding: 20px;
}

.room-img {
    width: 100%;
    margin-top: 40px;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

.menu {
    background-color: darkslateblue;
    padding: 15px;
    border-radius: 5px;
}

.menu a {
    color: white;
    padding: 10px;
}
</style>
