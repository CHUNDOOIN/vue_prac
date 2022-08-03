<template>
    <div v>
        <img :src="room.image" class="room-img" />
        <h4 @click="openModalSend">{{ room.title }}</h4>
        <p>{{ room.price.toLocaleString() }}원</p>
    </div>

    <!-- <div v-for="(roomData, i) in roomData" :key="i">

        <img :src="roomData.image" class="room-img" />
        <h4
            @click="
                isOpen = true;
                clickMove = i;
            "
        >
            {{ roomData.title }}
        </h4>
        <p>{{ roomData.price.toLocaleString() }}원</p> -->
</template>

<script>
export default {
    name: "Card",
    props: {
        isOpen: Boolean,
        room: Object,
        clickMove: Number,
    },
    methods: {
        openModalSend() {
            this.$emit("openModal", this.room.id);
        },
    },
};
</script>

<style></style>
