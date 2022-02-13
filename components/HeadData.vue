<template>
    <div class="head-data">
        <div class="head-data-item-f">
            <span class="head-item-text">Дата</span>
            <span class="head-item-data">{{new Date(tasks.date).toLocaleDateString()}}</span>
        </div>
        <div class="head-data-item">
            <span class="head-item-text">Размер</span>
            <span class="head-item-data">{{tasks.size}} мм</span>
        </div>
        <div class="head-data-item">
            <span class="head-item-text">Выдержа</span>
            <span 
                :style="[tasks.exposure > 100 ? redPrice : greenPrice]"
                class="head-item-data-x">{{tasks.exposure}} мин.</span>
        </div>
        <div class="head-data-item-l">
            <span class="head-item-text">Оборот</span>
            <span 
                :style="[tasks.turn > 100 ? redPrice : greenPrice]" 
                class="head-item-data-x">{{tasks.turn}} мин.</span>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            tasks: Array
        },
        data() {
            return {
                greenPrice: {
                    color: '#18CDB3'
                },
                redPrice: {
                    color: '#E73A82'
                },
            }
        },
    }
</script>

<style lang="scss" scoped>
@import 'static/style/styles.scss';

.head-data {
    height: auto;
    width: 100%;
    margin-top: 10px;
    @include flex-between-center;
}

.head-data-item-f {
    height: 95px;
    max-width: 294px;
    width: 100%;
    margin-left: 0px;
    margin-right: 0px;
    background: $main-white;
    box-shadow: $main-shadow;
    border-radius: $main-radius;
    @include flex-column-center-start;
}

.head-data-item {
    height: 95px;
    max-width: 294px;
    width: 100%;
    margin-left: 5px;
    margin-right: 5px;
    background: $main-white;
    box-shadow: $main-shadow;
    border-radius: $main-radius;
    @include flex-column-center-start;
}

.head-data-item-l {
    height: 95px;
    max-width: 294px;
    width: 100%;
    margin-left: 5px;
    margin-right: 0px;
    background: $main-white;
    box-shadow: $main-shadow;
    border-radius: $main-radius;
    @include flex-column-center-start;
}

.head-item-text {
    height: 15px;
    width: 100%;
    margin-left: 17px;
    margin-top: 10px;
    font-family: Rubik;
    font-style: normal;
    font-weight: 600;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: -0.025em;
    color: $main-dark-grey;
}

.head-item-data {
    height: auto;
    width: 100%;
    margin-top: 15px;
    padding-bottom: 4px;
    margin-left: 17px;
    font-family: Rubik;
    font-style: normal;
    font-weight: 300;
    font-size: 28px;
    line-height: 33px;
    letter-spacing: -0.04em;
    color: $main-dark-grey;
}
.head-item-data-x {
    height: auto;
    width: 100%;
    margin-top: 15px;
    padding-bottom: 4px;
    margin-left: 17px;
    font-family: Rubik;
    font-style: normal;
    font-weight: 600;
    font-size: 28px;
    line-height: 33px;
    letter-spacing: -0.04em;
    color: $main-dark-grey;
}
</style>