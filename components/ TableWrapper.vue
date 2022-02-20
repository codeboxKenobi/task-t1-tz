<template>
    <div class="app-wrapper">
        <div class="table-wrapper">
        <div class="melt">
            <div class="melt-number">Плавка: {{tasks.id}}</div>
            <div class="paginated">
                <button class="paginated-button" type="button">
                    <img @click="pageRevers" id="prev" src="/img/leftButton.svg" alt="">
                </button>
                <button class="paginated-button" type="button">
                    <img @click="pageRevers" id="next" src="/img/rightButton.svg" alt="">
                </button>
            </div>
        </div>
        <HeadData :tasks="tasks" />
        <Details :tasks="tasks" />
        <div class="chart-wrapper">
            <ChartData v-if="onload" :data="lineChartData" :options="lineChartOptions" style="width: 50%;" />
            <ChartData v-if="onload" :data="lineChartData2" :options="lineChartOptions" style="width: 50%;" />
        </div>
    </div>
    </div>
</template>

<script>
import ChartData from './ChartData.vue'

    export default {
        components: { ChartData },
        data() {
            return {
                onload: false,
                tasks: {},
                page: 0,
                dataCollection: [],
                
                lineChartData: {
                    labels: [
                        "Январь",
                        "Февраль",
                        "Март",
                        "Апрель",
                        "Май",
                        "Июнь",
                        "Июль",
                        "2Август",
                        "Сентябрь",
                        "Октябрь",
                    ],
                    datasets: [
                        {
                            label: "Visualizaciones",
                            data: [],
                            backgroundColor: "rgba(20, 255, 0, 0.3)",
                            borderColor: "rgba(100, 255, 0, 1)",
                            borderWidth: 2,
                        },
                    ],
                },
                lineChartData2: {
                    labels: [
                        "Январь",
                        "Февраль",
                        "Март",
                        "Апрель",
                        "Май",
                        "Июнь",
                        "Июль",
                        "2Август",
                        "Сентябрь",
                        "Октябрь",
                    ],
                    datasets: [
                        {
                            label: "Visualizaciones",
                            data: [],
                            backgroundColor: "rgba(20, 255, 0, 0.3)",
                            borderColor: "rgba(100, 255, 0, 1)",
                            borderWidth: 2,
                        },
                    ],
                },
                lineChartOptions: {
                    responsive: true,
                    legend: {
                        display: false,
                    },
                    title: {
                        display: true,
                        text: "2022",
                        fontSize: 24,
                        fontColor: "#6b7280",
                    },
                    tooltips: {
                        backgroundColor: "#17BF62",
                    },
                    scales: {
                        xAxes: [
                            {
                                gridLines: {
                                    display: true,
                                },
                            },
                        ],
                        yAxes: [
                            {
                                ticks: {
                                    beginAtZero: true,
                                    max: 100,
                                    min: 0,
                                    stepSize: 1,
                                },
                                gridLines: {
                                    display: true,
                                },
                            },
                        ],
                    },
                },
            }
        },
        methods: {
            async getData(data) {
                try {
                    this.onload = false
                    data == null ? data = 0 : data
                    let response = await fetch('../tasks.json')
                    let taskData = await response.json()
                    this.tasks = taskData[data]
                    this.onload = true
                } catch (error) {
                    console.log(error);
                }
            },
            pageRevers(event) {
                if (event.target.id == 'next') {
                    document.getElementById('prev').style.display = ''
                    this.getData(this.page++ + 1)
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
            }
        },
        beforeUpdate() {
            this.dataCollection = []
            this.getGraphData()
            this.lineChartData.datasets[0].data = this.dataCollection[0]    
            this.lineChartData2.datasets[0].data = this.dataCollection[1] 
        },
        mounted() {
            this.getData()
            if (this.page == 0) {
                this.lineChartData.datasets[0].data = this.dataCollection[0]
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
.chart-wrapper {
    margin-top: 10px;
    max-height: auto;
    height: 94%;
    max-width: 1200px;
    width: 100%;
    background: $main-white;
    box-shadow: $main-shadow;
    border-radius: $main-radius;
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