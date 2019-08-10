<template>

    <ul>
        <li v-bind:key="book.chapters.indexOf(chapter)" v-for="chapter in book.chapters" v-on:click="setChapter(chapter, book.name +' '+(1+book.chapters.indexOf(chapter)) )">

            <button class="bTtl" >{{book.name}} : {{(book.chapters.indexOf(chapter) + 1)}} </button>
            <p>{{chapter[0]}}</p>

        </li>
    </ul>
    
</template>
<script>
export default {
    name:'Chapters',
    props:['book'],
    methods:{
        setChapter(cpt, nm){
            this.$emit('event', [cpt,nm]);
        }
    }
    
}
</script>

<style scoped>
p{
	padding: 10px 5px;
	background:#eee;
	font-size: 5.5vw;
}
</style>