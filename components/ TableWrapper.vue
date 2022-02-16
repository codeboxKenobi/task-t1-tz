<template>
    <div class="app-wrapper">
        <div class="table-wrapper">
        <div class="melt">
            <div class="melt-number">Плавка: {{tasks.id}}</div>
            <div class="paginated">
                <button :disabled="prevButtonDisabled" @click="prev" class="paginated-button" type="button">
                    <img src="/img/leftButton.svg" alt="">
                </button>
                <button :disabled="nextButtonDisabled" @click="next" class="paginated-button" type="button">
                    <img src="/img/rightButton.svg" alt="">
                </button>
            </div>
        </div>
        <HeadData :tasks="tasks" />
        <Details :tasks="tasks" />
        <Graph :tasks="tasks" />
    </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                tasks: {},
                page: '',
                prevButtonDisabled: false,
                nextButtonDisabled: false,
            }
        },
        methods: {
            async getData(data) {
                try {
                    data == null ? data = 0 : data
                    let response = await fetch('../tasks.json')
                    let taskData = await response.json()
                        this.tasks = taskData[data]
                } catch (error) {
                    console.log(error);
                }
            },
     
            next() {
                console.log(this.page);
                if (this.page == 2) {
                    this.nextButtonDisabled = true
                } else {
                    this.nextButtonDisabled = false
                    this.prevButtonDisabled = false
                    this.getData(this.page++ + 1)
                }
            },
            prev() { 
                console.log(this.page); 
                if (this.page == 0) {
                    this.prevButtonDisabled = true
                } else {
                    this.nextButtonDisabled = false
                    this.prevButtonDisabled = false
                    this.getData(this.page-- - 1)
                }
            }
        },
        mounted() {
            this.getData()
        }
    }
</script>

<style lang="scss" scoped>
@import 'static/style/styles.scss';

.app-wrapper {
    height: auto;
    width: 100%;
    padding-bottom: 20px;
    background-color: #F1F3F6;
    @include flex-center-center;
}


.table-wrapper {
    margin-top: 10px;
    max-height: auto;
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