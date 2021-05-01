<template>
    <div class="about">
        <div style="display: flex; justify-content: center; align-items: center;">
            <h1 style="margin-right: 10px">{{ data["Name"] }} - <span :style="`color: ${tickerColor}`">{{ data["Price"] }}</span></h1>
            <h3 :style="`color: ${tickerColor}`">{{ data["Change"][1] }}</h3>
        </div>
        <h3>Pre-Market: {{ data["Pre-Market Price"] }}</h3>
        <p>Previous Close: {{ data["Previous Close"] }}</p>
        <p>Open: {{ data["Open"] }}</p>
        <p>Bid: {{ data["Bid"] }}</p>
        <p>Ask: {{ data["Ask"] }}</p>
        <p>Day's Range: {{ data["Day's Range"] }}</p>
        <p>52 Week Range: {{ data["52 Week Range"] }}</p>
        <p>Volume: {{ data["Volume"] }}</p>
        <p>Avg. Volume: {{ data["Avg Volume"] }}</p>
        <p>Market Cap: {{ data["Market Cap"] }}</p>
        <p>Beta (5Y Monthly): {{ data["Beta (5Y Monthly)"] }}</p>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    props: {
        ticker: String
    },
    data() {
        return {
            data: '',
            tickerColor: "gray"
        };
    },
    methods: {
        getData() {
            const path = `http://127.0.0.1:5000/${this.ticker}`;
            console.log(path)
            setInterval(() => {
                axios.get(path)
                    .then((res) => {
                        this.data = res.data;
                        if (this.data["Change"][1][0] === "+") {
                            this.tickerColor = "green"
                        } else if (this.data["Change"][1][0] === "-") {
                            this.tickerColor = "red"
                        }
                    })
                    .catch((error) => {
                        // eslint-disable-next-line
                        console.error(error);
                    });
                    error => {
        if (!error.response) {
            console.log("Please check your internet connection.");
        }

        return Promise.reject(error)
    }
            }, 10000);
        },
    },
    created() {
        this.getData();
    }
}
</script>

<style scoped>
.about {
    border-radius: 50px;
    background: #e6e6e6;
    box-shadow: 20px 20px 60px #c4c4c4, -20px -20px 60px #ffffff;
    padding: 35px;
    width: 50vw;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}

@media only screen and (max-width: 1280px) {
  .about {
    width: 80vw;
    box-shadow: none;
  }
}
</style>