<template>
    <div class="table-wrapper">
        <div class="melt">
            <div class="melt-number">Плавка: {{meltData}}</div>
            <div class="paginated">
                <button class="paginated-button" type="button">
                    <img src="/img/leftButton.svg" alt="">
                </button>
                <button class="paginated-button" type="button">
                    <img src="/img/rightButton.svg" alt="">
                </button>
            </div>
        </div>
        <HeadData />
    </div>
</template>

<script>
    export default {
        data() {
            return {
                meltData: 338110,
            }
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
    @include flex-start-center;
}
.paginated {
    height: 35px;
    width: 70px;
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