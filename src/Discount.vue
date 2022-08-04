<template>
    <div class="discount">
        <h4>지금 결제하면 {{ discount }}% 할인</h4>
    </div>
</template>

<script>
export default {
    name: "Discount",
    data() {
        return {
            discount: 30,
        };
    },
    mounted() {
        const timer = setInterval(() => {
            this.discount--;
            console.log(`${this.discount}%`);

            if (this.discount === 0) {
                console.log(`종료합니다.`);
                clearInterval(timer);
            }
        }, 1000);
    },
};
</script>

<style>
.discount {
    background-color: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}
</style>
