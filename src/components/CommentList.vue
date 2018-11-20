<template>
    <div id="comment-list">        
        <div class="comment-list-container">            
            <ul class="container">
                <li v-for="o in list" :key="o.seq">
                    <div class="comment-info">
                        <h4>{{o.nick}}</h4>
                        <span>작성일: {{o.data}}</span>
                    </div>
                    <div class="comment-desc">
                        <span>{{o.commentDesc}}</span>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    export default {
        props: ["list"]     
    }
</script>

<style scoped>

#comment-list {
    margin: 0 0.12rem;
    margin-bottom: 2rem;
}

.comment-list-container {
    border: 1px solid #aaa;
    padding: 7px 7px 7px 7px;
}

.container {
    margin: 0;
    padding: 0;
    list-style-type: none;    
}

.container li {
    padding: 7px 0;
    border-bottom: 1px solid #cbcbcb;
}

.container li:last-child {    
    border-bottom: 0;
}

.comment-info {    
    display: flex;    
    justify-content: space-between;
    align-items: center;
}

.comment-info h4 {
    margin: 0;
    line-height: 17px;
    font-size: 0.95rem;
}

.comment-info span {
    font-size: 0.75rem;    
}

.comment-desc {
    margin: 6px 0;
    padding: 8px 0;
    font-size: 0.85rem;
}


</style>