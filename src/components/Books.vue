<template>
    <div>
        <Ul>
            <li v-bind:key="bbl.indexOf(book)" v-for="book in bbl"><button class="bTtl" v-on:click="setBook(book)">{{ book.name }}</button></li>
        </Ul>
    </div>
</template>

<script>
    export default {
        name: 'Books',
        props: ['bbl'],
        methods:{
            setBook(bk){
                this.$emit('clkd', bk)
            },
        },
    }


</script>
    