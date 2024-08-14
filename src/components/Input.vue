<template>
    <div>
        <input min="0" type="number" @input="changeAmount($event.target.value)" placeholder="How much you want exchange?">
        <div>
            <button @click="convert()">Exchange</button>
            <button @click="favorite()">Favorite</button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        changeAmount: {
            type: Function,
            required: true
        },
        convert: {
            type: Function,
            required: true
        },
        favorite: {
            type: Function,
            required:true
        }
    }
}
</script>

<style scoped>
div {
    margin-top: 3em;
}
input {
    border: 0;
    padding: 10px 15px;
    background: none;
    color: white;
    border-bottom: 2px solid #fafafa;
    outline: none;
    width: 500px;
    font-size: 1.2em;
}
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

button {
    padding: 15px 20px;
    text-transform: uppercase;
    cursor: pointer;
    background: #767571;
    border-radius: 3px;
    border: 0;
    margin: .5rem;
}
button:hover {
    font-weight: bold;
    color: whitesmoke;
}
</style>