<template>
    <div class="graph">
        <canvas class="myChart" id="myChart"></canvas>
    </div>
</template>


<script>
import { Chart } from 'chart.js'

    export default {
        
        props: {
            dataCollection: {
                type: Array
            }
        },
        data() {
            return {
                firstLine: [],
                secondLine: []
            }
        },  
        beforeMount() {
            this.firstLine = this.dataCollection[0]
            this.secondLine = this.dataCollection[1]
        },
        mounted() {
            console.log(this.firstLine);
            this.insertChar()
            
        },  
        methods: {
            insertChar() {
                const ctx = document.getElementById('myChart').getContext('2d');
                const myChart = new Chart(ctx, {
                    type: 'line',
                    data: {
                        labels: ["Январь", "Февраль", "Март", "Апрель", "Май", "Июнь", "Июль", "Август", "Сентябрь", "Октябрь","Ноябрь", "Декабрь"],
                        datasets: [{ 
                            data: this.firstLine,
                            label: "Year1",
                            borderColor: "rgb(62,149,205)",
                            backgroundColor: "rgb(62,149,205,0.1)",
                            borderWidth:2
                        },
                        { 
                            data: this.secondLine,
                            label: "Year2",
                            borderColor: "rgb(62,19,205)",
                            backgroundColor: "rgb(62,149,205,0.1)",
                            borderWidth:2
                        }]
                    }, 
                })
            },
        },        
    }
</script>

<style lang="scss" scoped>
@import 'static/style/styles.scss';

.graph {
    height: auto;
    max-width: 1200px;
    width: 100%;
    margin-top: 10px;
    background: $main-white;
    box-shadow: $main-shadow;
    border-radius: $main-radius;
    @include flex-column-start-center;
}

.myChart {
    height: 100%;
    width: 100%;

}
</style>