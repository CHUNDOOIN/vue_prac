<template>
    <transition name="fade">
        <Modal
            @closeModal="
                isOpen = false;
                clickMove = $event;
            "
            :room="myRoomData"
            :isOpen="isOpen"
            :clickMove="clickMove"
        />
    </transition>

    <div class="menu">
        <a v-for="a in menu" :key="a">{{ a }}</a>
    </div>

    <Discount v-if="showDiscount === true" />

    <div class="btn-box">
        <button @click="minSort">최저가순</button>
        <button @click="maxSort">최고가순</button>
        <button @click="abcSort">가나다순</button>
        <button @click="fiftySort">50만 이하</button>
        <button @click="sortBack">되돌리기</button>
    </div>

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
            showDiscount: true,
            clickMove: 0,
            myRoomDataOriginal: [...roomData],
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

        sortBack() {
            this.myRoomData = [...this.myRoomDataOriginal];
        },
        minSort() {
            this.myRoomData.sort((a, b) => a.price - b.price);
            console.log("최저가순 정렬 완료");
        },
        maxSort() {
            this.myRoomData.sort((a, b) => b.price - a.price);
            console.log("최고가순 정렬 완료");
        },
        abcSort() {
            this.myRoomData.sort((a, b) => (a > b ? 1 : -1));
            // console.log(this.myRoomData[0].title[0]);
            console.log("가나다순 정렬 완료");
        },
        fiftySort() {
            this.myRoomData = this.myRoomData
                .filter((el) => el.price <= 500000)
                .sort((a, b) => a.price - b.price);
        },
    },
    // mounted() {
    //     setTimeout(() => {
    //         this.showDiscount = false;
    //     }, 2000);
    // },
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

/* 모달창 애니메이션 */
.fade-enter-from {
    transform: translateY(-1000px);
}
.fade-enter-active {
    transition: all 1s;
}
.fade-enter-to {
    transform: translateY(0px);
}

.fade-leave-from {
    opacity: 1;
}
.fade-leave-active {
    transition: all 1s;
}
.fade-leave-to {
    opacity: 0;
}

.btn-box {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
}
</style>
