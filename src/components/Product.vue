<template>
    <div id="product">
        <div class="raman-image">
            <img src="../assets/1454D91649AF30F91B.jpg" alt="">            
        </div>
        <hr>
        <div class="raman-description">
            <h3>라면 이름 - {{product.name}}</h3>
            <p>제조사 - {{product.manufacturer}}</p>
            <p>원산지 - {{product.origin}}</p>
            <p>특징 - {{product.desc}}</p>
        </div>
    </div>
</template>

<script>
    export default {
        props: ["product"],
    }
</script>

<style>

#product {
    margin-bottom: 2rem;
    border: 3.5px solid #5a6268;    
}

#product hr {
    margin: 10px 10px;
    border: 0.5px solid #aaa;
}

.raman-image {     
    text-align: center;
    margin-right: 4.43px;    
}

.raman-image img {
    width: 300px;
    height: 300px;
}

.raman-description { 
    padding-left: 10px;
}

@media (min-width:415px) {
    #product {    
        border-top: 5px solid #5a6268;   
        display: flex; 
    }

    #product hr {        
        margin: 10px 10px;
    }

    .raman-image { 
        flex: 2;
        text-align: center;
        margin-right: 4.43px;    
    }

    .raman-image img {
        width: 350px;
        height: 400px;
    }

    .raman-description { 
        flex: 1;
    }


}



</style>