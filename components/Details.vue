<template>
    <div class="details">

        <div class="melt-table">
            <div class="melt-table-head-text">Сводная таблица</div>
        </div>
        <div class="melt-table-descript">
            <div class="melt-table-descript-item-f"><span class="descript-item-text" >Агрегат</span></div>
            <div class="melt-table-descript-item"><span class="descript-item-text" >Дата</span></div>
            <div class="melt-table-descript-item"><span class="descript-item-text" >Начало</span></div>
            <div class="melt-table-descript-item"><span class="descript-item-text" >Длительность, мин.</span></div>
            <div class="melt-table-descript-item"><span class="descript-item-text" >Простой</span></div>
            <div class="melt-table-descript-item-l"><span class="descript-item-text" >Тип</span></div>
        </div>
        <div v-for="items in tasks.details" :key="items.id" class="melt-table-data-line">
            <div class="descript-item-f"><span class="descript-item-text" >{{items.unit}}</span></div>
            <div class="descript-item">
                <span class="descript-item-text" >
                    {{ getDate(items.date)}}
                </span>
            </div>
            <div class="descript-item"><span class="descript-item-text" >{{getDate(items.start)}}</span></div>
            <div class="descript-item"><span class="descript-item-text" >{{items.length}}</span></div>
            <div class="descript-item">
                <span :class="[items.idle ? 'redPrice' : 'greenPrice']" class="descript-item-text" >
                    {{ items.idle ? 'Да' : 'Нет' }}
                </span>
            </div>
            <div class="descript-item-l"><span class="descript-item-text" >{{items.type}}</span></div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            tasks: {
                type: Object
            }
        },
        methods: {
            getDate(dateInFormat) {
                return new Date(dateInFormat).toLocaleDateString()
            }
        },
    }
</script>

<style lang="scss" scoped>
@import 'static/style/styles.scss';

.details {
    min-height: 400px;
    max-width: 1200px;
    width: 100%;
    margin-top: 10px;
    background: $main-white;
    box-shadow: $main-shadow;
    border-radius: $main-radius;
    @include flex-column-start-center;
}

.melt-table {
    height: 50px;
    width: 100%;
    @include flex-between-center;
}

.melt-table-head-text {
    height: 28px;
    width: 166px;
    margin-left: 16px;
    @include flex-start-center;
    font-family: Rubik;
    font-style: normal;
    font-weight: 600;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: -0.025em;
    color: $main-grey;
}

.melt-table-descript {
    height: 54px;
    width: 100%;
    @include flex-between-center;
}

.melt-table-descript-item {
    height: 40px;
    width: 196px;
    margin-left: 2px;
    margin-right: 2px;
    background-color: $descript-item;
    @include flex-start-center;
    font-family: Rubik;
    font-style: normal;
    font-weight: 600;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: -0.025em;
    color: $main-grey;
}

.melt-table-descript-item-f {
    height: 40px;
    width: 196px;
    margin-left: 16px;
    margin-right: 2px;
    background-color: $descript-item;
    @include flex-start-center;
    font-family: Rubik;
    font-style: normal;
    font-weight: 600;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: -0.025em;
    color: $main-grey;
}

.melt-table-descript-item-l {
    height: 40px;
    width: 196px;
    margin-left: 2px;
    margin-right: 16px;
    background-color: $descript-item;
    @include flex-start-center;
    font-family: Rubik;
    font-style: normal;
    font-weight: 600;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: -0.025em;
    color: $main-grey;
}

.descript-item-text {
    margin-left: 16px;
}

.melt-table-data-line {
    height: 40px;
    width: 100%;
    @include flex-between-center;
    // border-bottom: $item-line-color;
}

.descript-item {
    height: 40px;
    width: 196px;
    margin-left: 2px;
    margin-right: 2px;
    @include flex-start-center;
    font-family: Rubik;
    font-style: normal;
    font-weight: normal;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: -0.025em;
    color: $main-grey;
    border-bottom: $item-line-color;
}

.descript-item-f {
    height: 40px;
    width: 196px;
    margin-left: 16px;
    margin-right: 2px;
    @include flex-start-center;
    font-family: Rubik;
    font-style: normal;
    font-weight: normal;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: -0.025em;
    color: $main-grey;
    border-bottom: $item-line-color;
}

.descript-item-l {
    height: 40px;
    width: 196px;
    margin-left: 2px;
    margin-right: 16px;
    @include flex-start-center;
    font-family: Rubik;
    font-style: normal;
    font-weight: normal;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: -0.025em;
    color: $main-grey;
    border-bottom: $item-line-color;
}

.greenPrice {
    color: #18CDB3;
}
.redPrice {
    color: #E73A82;
}
</style>