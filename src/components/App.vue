<template>
  <div id="app">
    <div id="header">
      <h1>Biblia</h1>
    </div>
    <div v-if="book==null">
      <Books :bbl=bbl @clkd='loadBook' />
    </div>
    <div v-else-if="chapter==null">
      <Chapters :book=book @event="loadChapter"/>
      <button class="goBack" v-on:click="goBack(0)">VOLTAR</button>
    </div>
    <div v-else>
      <Main :chapter=chapter :name=cName />
      <div class="holder">
          <button v-on:click='copyContent'>COPIAR</button>
      </div>
      <button class="goBack" v-on:click="goBack(1)">VOLTAR</button>
    </div>

    
    <div class="bottom">
      by MarceloJCS
    </div>
  </div>
</template>

<script>
  import json from '../data/data.json';
  import Books from './Books';
  import Chapters from './Chapters';
  import Main from './Main';
  export default {
    name: 'app',
    components:{
      Books,
      Chapters,
      Main,
    },
    methods:{
      loadBook(bk){
          this.book=bk;
          window.scrollTo(0,0);

      },
      loadChapter(cpt){
        this.chapter=cpt[0];
        this.cName=cpt[1];
        window.scrollTo(0,0);

      },
      goBack(id){
        switch(id){
          case 0 :
            this.book=null;
            break;
            case 1:
              this.chapter=null;
              break
        }
        window.scrollTo(0,0)

      },
      copyContent(){
          const range = document.createRange();
          range.selectNode(document.querySelector('#main'));
          window.getSelection().removeAllRanges()
          window.getSelection().addRange(range);
          document.execCommand("Copy");
          window.getSelection().removeAllRanges()
      }
    } ,
    data(){
      return{
        bbl:json,
        book:null,
        chapter:null,
        cName:'',
      }
    }
  }

</script>

<!-- CSS libraries -->
<style src="reset.css/reset.css"></style>

<!-- Global CSS -->
<style>
h1{
	background: #333333;
	color:#fff;
	padding:10px;
	font-size:10vw;
	font-weight: bold!important;
	
}

.bTtl{
	width:100vw;
	text-align: left;
	background: none;
	margin: 10px 0 0 0;
	border:solid 1px #888; 
	border-top:none;
	border-left:none;
	font-size: 6vw
}

.bottom{
	font-size: 3vw;
	color:#ffffff;
	background:#333333;
	padding:5px
}

.goBack{
	background:#333;
	border:none;
	padding: 10px;
	font-weight:bold;
	color : #fff;
	margin:10px;
	font-size:5.7vw
}

.holder{
	text-align:center;
	margin: 10px;

}
.holder button{
	display:inline-block;
	background:#383;
	color:#ffff;
	font-size:6vw;
	padding:10px;
	border:none;
}
</style>
