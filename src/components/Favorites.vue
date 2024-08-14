<template>
    <div className="favorites_wrapper">
        <h3>Favorites cryptocurrency</h3>
        <div v-for="fav,index in favs" :key="index" @click="getFromFavorites(index)">
            <p>{{ fav.from }} - {{ fav.to }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        favs: {
            type: Array,
            required: true
        },
        getFromFavorites: {
            type: Function,
            required: true
        }
    }
}
</script>

<style scoped>
.favorites_wrapper {
    margin: 0 auto;
}
h3 {
    color: whitesmoke;
}
div {
    width: 20em;
    transition: all 500ms ease;
}
p {
    padding: 10px 15px;
    color: whitesmoke;
    border-bottom: 1px solid #fafafa;
}

div:hover {
    opacity: .7;
    transform: scale(1.1);
    cursor: pointer;
}
</style>