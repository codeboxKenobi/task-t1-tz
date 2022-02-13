<template>
    <div class="table-wrapper">
        <div class="melt">
            <div class="melt-number">Плавка: {{tasks.id}}</div>
            <div class="paginated">
                <button @click="prev" class="paginated-button" type="button">
                    <img src="/img/leftButton.svg" alt="">
                </button>
                <button @click="next" class="paginated-button" type="button">
                    <img src="/img/rightButton.svg" alt="">
                </button>
            </div>
        </div>
        <HeadData :tasks="tasks" />
        <Details :tasks="tasks" />
    </div>
</template>

<script>
    export default {
        data() {
            return {
                tasks: [],
                page: 0
            }
        },
        methods: {
            async getData(dta) {
                if (dta == null ) {
                    dta = 0
                }
                let response = await fetch('../tasks.json')
                let taskData = await response.json()
                    this.tasks = taskData[dta]
                    console.log(this.tasks);
                    console.log();
            },
            next() {
                this.getData(this.page++ + 1)
            },
            prev() {
                this.getData(this.page-- - 1)
            }
        },
        mounted() {
            this.getData()
        }
    }
</script>

<style lang="scss" scoped>
@import 'static/style/styles.scss';


.table-wrapper {
    max-height: 694px;
    height: 94%;
    max-width: 1200px;
    width: 94%;
    @include flex-column-start-center;
}
// =======================================MELT=============================
.melt {
    height: 54px;
    width: 100%;
    background: $main-white;
    box-shadow: $main-shadow;
    border-radius: $main-radius;
    @include flex-between-center;
}
.melt-number {
    height: 28px;
    width: 166px;
    margin-left: 16px;
    color: $main-dark-grey;
    @include flex-start-center;
}
.paginated {
    height: 35px;
    width: 71px;
    margin-right: 16px;
    @include flex-between-center;
}
.paginated-button {
    height: 35px;
    width: 35px;
    border: none;
    outline: none;
    @include flex-center-center;
}
// =======================================MELT=============================
</style>