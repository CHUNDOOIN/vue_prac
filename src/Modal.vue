<template>
    <div class="black-bg" v-if="isOpen">
        <div class="white-bg">
            <img :src="room[clickMove].image" style="width: 100%" />
            <h4>{{ room[clickMove].title }}</h4>
            <p>{{ room[clickMove].content }}</p>
            <!-- <input @input="month = $event.target.value" /> -->
            <input v-model="month" />
            <input type="range" min="1" max="12" v-model="month" />

            <p>
                {{ month }}개월 선택함 :
                {{ Number(room[clickMove].price * Number(month)) }}원
            </p>
            <button @click="closeSend">닫기</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Modal",
    data() {
        return {
            month: 1,
        };
    },

    watch: {
        month(a) {
            if (isNaN(a) === true) {
                alert("숫자가 아닌데요?");
                this.month = 1;
            }

            if (a >= 13) {
                alert("최대 12개월!!!");
                this.month = 1;
            }
        },
    },
    props: {
        room: Array,
        isOpen: Boolean,
        clickMove: Number,
    },
    methods: {
        closeSend() {
            this.$emit("closeModal", this.room.id);
        },
    },
    components: {},
};
</script>

<style></style>
