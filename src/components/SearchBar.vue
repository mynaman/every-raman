<template>
    <div id="search" ref="search">
        <div class="search-bar">
            <input type="text" class="search-input" name="ramanName" v-model="ramanName" placeholder="라면 검색" @keyup.enter="ramanSearch">
            <button type="button" class="search-btn" @click="ramanSearch">검 색</button>
        </div>
    </div>
</template>

<script>
    import eventBus from '../EventBus'

    export default {
        data: function() {
            return {
                ramanName: ""
            }
        },        
        methods: {
            ramanSearch : function() {                
                if(this.ramanName.length < 2) {
                    alert("두글자 입력 해주세요");                    
                } else {
                    eventBus.$emit("searchSubmit", this.ramanName);
                    this.$refs.search.classList.add("raise");
                }
            }
        }        
    }
</script>
<style>

#search {
    margin: 38% 0.12rem;
}

#search.raise {
    margin: 2.5rem 0.12rem;
    margin-bottom: 2rem;   
}

.search-bar {
    display: flex;
    height: 8vh;
}

.search-input {
    flex: 3;
    margin-right: 4.43px;
    padding: 0;
    border: 0;    
    background-color:#FFE4E1;
    color: #000;
    font-weight: 900;
    font-size: 1.8rem;
    border-radius: 5px;
    text-align: center;
    outline-style: none;
    letter-spacing: 1.5px;
}

.search-btn {
    flex: 1;
    border-radius: 5px;
    border: 1px solid #aaa;;
    color: #5a6268;    
    background-color: #fff;;
    font-weight: 900;
    font-size: 1.2rem;
    outline-style: none;
    cursor: pointer;
}

.search-btn:hover {
    background-color: #aaa;;
    color: #fff;
}


@media (max-width:415px) {
    .search-input, .search-btn {
        font-size: 1rem;    
    }

}

</style>