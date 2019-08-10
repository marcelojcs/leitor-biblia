<template>
    <div id='main'>
        <h2>{{name}}</h2>
        <ol>
            <li v-for="verse in chapter" v-bind:key="chapter.indexOf(verse)">
                <p>
                   {{1+chapter.indexOf(verse)}}. {{verse}}
                </p>
            </li>
        </ol>
    </div>
</template>
<script>
    export default {
        name:'Main',
        props:['chapter','name']
    }
</script>

<style scoped>
#main{
    font-size: 5.5vw;
    overflow: hidden;

}
ol{  
    list-style-type:none;

    }
li{
  
    margin: 10px 0px;
}

h2{
    padding: 5px;
    font-size:7vw;
    font-weight:bold;
}
</style>