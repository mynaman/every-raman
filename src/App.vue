<template>
  <div id="app">
    <div id="wrap">
      <search-bar></search-bar>
      <div id="setion" v-if="isProduct()">
        <product :product="product"></product>
        <comment></comment>
        <comment-list :list="list"></comment-list>
      </div>
    </div>
  </div>
</template>

<script>
  import SearchBar from './components/SearchBar';
  import Product from './components/Product';
  import Comment from './components/Comment';
  import CommentList from './components/CommentList';
  import eventBus from './EventBus';

  const list = [
    { seq: 0, nick:"mynaman", data: "2018.11.20 20:06:12", commentDesc: "안녕하세요!"},
    { seq: 1, nick:"평택칸나바로", data: "2018.11.21 05:22:15", commentDesc: "반갑습니다!"},
    { seq: 2, nick:"송림동카카", data: "2018.11.22 23:11:54", commentDesc: "어디서 오셨어요?"},
  ]

  export default {
    name: "app",
    components: { SearchBar, Product, Comment, CommentList },
    data: function(){
      return {
        product : null,
        list : list,
      }
    },    
    methods: {
      isProduct: function() {
        return !this.product ? false : true;
      },
      productSelect: function(name) {
        if(name === "신라면블랙") this.product = { img: "/img/1511741838357.jpg", name:'신라면 블랙', manufacturer: '농심', origin: '한국', desc: '2등라면'};
        if(name === "신라면") this.product = { img: "1454D91649AF30F91B.jpg", name:'신라면', manufacturer: '농심', origin: '한국', desc: '농심 신라면은 우리 입맛에 맞는 얼큰하고 매운맛 제품으로 농심의 정성과 앞선 기술 그리고 좋은 원료로 만들어 남녀노소 구분없이 많은 사랑을 받는 제품입니다. 또한, 세계 여러나라에 수출하여 한국의 맛을 세계화 시키는 데 앞장서고 있습니다.'};
      },
      commentPost: function(comment) {
        const num = this.list.length;        
        const add = { seq:num, data: "2018.11.25 11:11:11" };
        const commentOnce = {...comment, ...add };
        this.list = this.list.concat(commentOnce);        
      }
    },    
    mounted: function() {
      eventBus.$on("searchSubmit", (name) => {
        this.productSelect(name);
      }),
      eventBus.$on("commentSubmit", (comment) => {
        this.commentPost(comment);        
      })
    }
    
  }
</script>

<style>

body { 
  margin: 0; 
  padding: 1.5rem 0;
  background-color:#4c677c }

#app {
  margin: 0 auto;
  max-width: 1024px;
  background-color: #fff;
  
}

#wrap {
  padding: 10px;
  height: auto;
  
}

</style>