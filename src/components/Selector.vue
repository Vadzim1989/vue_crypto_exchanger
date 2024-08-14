<template>
    <div>
        <ul>
            <li :class="cryptoCurrency == 'BTC'  ? 'active' : ''" @click="setCrypto('BTC')">Bitcoin</li>
            <li :class="cryptoCurrency == 'ETH'  ? 'active' : ''" @click="setCrypto('ETH')">ETH</li>
            <li :class="cryptoCurrency == 'USDT' ? 'active' : ''" @click="setCrypto('USDT')">USDT</li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        setCrypto: {
            type: Function,
            required: true
        },
        cryptoCurrency: {
            type: String,
            required: true 
        }
    }
}
</script>

<style scoped>
div {
    border-radius: 3px;
    border: 3px solid white;
}
ul {
    list-style: none;
    width: 200px;
    padding: 0;    
}
li {
    display: block;
    background: none;
    color: whitesmoke;
    padding: 20px 0;
}
li:hover, li.active {
    cursor: pointer;
    color: black;
    background: #767571;
}
</style>