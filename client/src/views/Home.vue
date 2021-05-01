<template>
    <div class="home">
        <div class="container">
            <div style="font-size: 36px;"><b>Stock Tracker</b></div>
            <div class="search-bar">
                <input placeholder="i.e. GME" class="search" type="text" v-model="ticker" required/>
                <router-link class="button" :to="{ name: 'Ticker', params: { ticker: this.ticker } }">Check</router-link>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            ticker: ''
        };
    }
};
</script>

<style>
body {
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

.search-bar {
    width: 100vw;
    display: flex;
    padding: 5px 5px 5px 5px;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.search {
    border: none;
    height: 80px;
    border-radius: 8px;
    width: 240px;
    background: #e6e6e6;
    border: 1px solid rgb(0, 0, 0, 0.2);
    padding-left: 10px;
    margin-bottom: 20px;
    font-size: 24px;
}

.button {
    border-radius: 8px;
    background: #e6e6e6;
    box-shadow: 20px 20px 60px #c4c4c4, -20px -20px 60px #ffffff;
    width: 255px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    color: black;
}

.button:active {
    background: #e6e6e6;
    box-shadow: inset 20px 20px 60px #c4c4c4, inset -20px -20px 60px #ffffff;
    color: black;
}
</style>

