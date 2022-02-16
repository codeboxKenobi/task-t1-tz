<template>
    <div class="app-wrapper">
        <div class="table-wrapper">
        <div class="melt">
            <div class="melt-number">Плавка: {{tasks.id}}</div>
            <div class="paginated">
                <button @click="pageRevers" class="paginated-button" type="button">
                    <img id="prev" src="/img/leftButton.svg" alt="">
                </button>
                <button @click="pageRevers" class="paginated-button" type="button">
                    <img id="next" src="/img/rightButton.svg" alt="">
                </button>
            </div>
        </div>
        <HeadData :tasks="tasks" />
        <Details :tasks="tasks" />
        <Graph :dataCollection="dataCollection" />
    </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                tasks: {},
                page: 0,
                dataCollection: []
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
            pageRevers(event) {
                    if (event.target.id == 'next') {
                        document.getElementById('prev').style.display = ''
                         this.getData(this.page = this.page++ + 1)
                         if (this.page == 2) {
                             event.target.style.display = 'none'
                         }
                    }
                    else if (event.target.id == 'prev') {
                        document.getElementById('next').style.display = ''
                        this.getData(this.page-- - 1)
                        if (this.page == 0) {
                             event.target.style.display = 'none'
                         }
                    }
            },
            getGraphData() {
                this.dataCollection.push(this.tasks.graph.map(item => item[0]))
                this.dataCollection.push(this.tasks.graph.map(item => item[1]))
                console.log(this.dataCollection);
            }
        },
        beforeUpdate() {
            this.getGraphData()
        },
        mounted() {
            this.getData()
            if (this.page == 0) {
                document.getElementById('prev').style.display = 'none'
            }
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
    border-radius: 10px;
    @include flex-between-center;
}
.paginated-button {
    height: 35px;
    width: 35px;
    background-color: transparent ;
    border: none;
    outline: none;
    @include flex-center-center;
}
// =======================================MELT=============================
</style>