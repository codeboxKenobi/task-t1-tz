<template>
    <div class="head-data">
        <div class="head-data-item-f">
            <span class="head-item-text">Дата</span>
            <span class="head-iten-data">12.08.22</span>
        </div>
        <div class="head-data-item">
            <span class="head-item-text">Размер</span>
            <span class="head-iten-data">100х400 мм</span>
        </div>
        <div class="head-data-item">
            <span class="head-item-text">Выдержа</span>
            <span class="head-iten-data">60 мин.</span>
        </div>
        <div class="head-data-item-l">
            <span class="head-item-text">Оборот</span>
            <span class="head-iten-data">115 мин.</span>
        </div>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>
@import 'static/style/styles.scss';

.head-data {
    height: 95px;
    width: 100%;
    margin-top: 10px;
    @include flex-between-center;
}
.head-data-item-f {
    height: 100%;
    max-width: 294px;
    width: 100%;
    margin-left: 0px;
    margin-right: 5px;
    background: $main-white;
    box-shadow: $main-shadow;
    border-radius: $main-radius;
    @include flex-column-center-start;
}
.head-data-item {
    height: 100%;
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
    height: 100%;
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
    font-family: Rubik;
    font-style: normal;
    font-weight: normal;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: -0.025em;
}
.head-iten-data {
    height: 15px;
    width: 100%;
    margin-top: 18px;
    margin-left: 17px;
    font-family: Rubik;
    font-style: normal;
    font-weight: 300;
    font-size: 28px;
    line-height: 33px;
    letter-spacing: -0.04em;
}
</style>