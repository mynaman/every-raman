<template>
    <div id="comment">
        <div class="comment-container">
            <div class="comment-id">
                <h4>댓글 쓰기</h4>
                <input type="text" name="id" v-model="comment.nick" placeholder="닉네임 입력">
            </div>
            <div class="comment-post">
                <textarea name="commentDesc" class="commentDesc" v-model="comment.commentDesc" rows="4" placeholder="댓글 입력"></textarea>                
                <button type="button" class="comment-btn" @click="commentPost">등 록</button>
            </div>            
        </div>
    </div>
</template>

<script>
    import eventBus from '../EventBus'   

    export default {        
        data: function() {
            return {
                comment: {
                    nick: "",
                    commentDesc: "",
                }
            }
        },
        methods: {
            commentPost: function() {
                eventBus.$emit("commentSubmit", this.comment);
                this.comment.nick = "";
                this.comment.commentDesc = "";
            }
        }        
    }
</script>

<style scoped>

#comment{
    margin: 0 0.12rem;
    margin-bottom: 2rem;
}

.comment-container {
    border: 1px solid #aaa;    
    padding: 7px 7px 7px 7px;    
}

.comment-id h4 {
    margin: 0;
    margin-bottom: 7px;
}

.comment-id input{
    border:1px solid #aaa;
    outline-style: none;
    margin-bottom: 5px;
    padding-left: 4px;
    line-height: 30px;
}

.comment-post {
    display: flex;
}

.comment-post .commentDesc {
    flex: 2;
    margin-right: 4px;
    border:1px solid #aaa;
    outline-style: none;
    resize:none;
}

.comment-post .comment-btn {
    flex: 1;
    border-radius: 5px;
    border: 1px solid #aaa;;
    color: #5a6268;    
    background-color: #fff;
    font-weight: 900;
    font-size: 1.2rem;
    outline-style: none;
    cursor: pointer;
}

.comment-post .comment-btn:hover {
    background-color: #28a745;
    color: #fff;
}

</style>