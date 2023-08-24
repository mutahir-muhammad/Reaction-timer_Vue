<template>
    <div>
        <p>Reaction Time is {{ score }} ms</p>
        <p class="rank">{{ rank }}</p>
    </div>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = "Noice!"
        }
        else if (this.score < 400) {
            this.rank = "Great Reflexes!"
        }
        else {
            this.rank = "Slowpoke...try again later :)"
        }
    }
}
</script>

<style>
.rank {
    font-size: 22px;
    color: rgb(25, 213, 138);
    font-weight: bold;
}
</style>