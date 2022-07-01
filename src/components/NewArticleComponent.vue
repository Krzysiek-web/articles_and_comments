<template>
    <div class="new-article-container">
        
            <input id="title" v-model="title" type="text" class="form-control title" placeholder="Tytuł"/>
          
       
        
            <textarea id="context" v-model="content" type="text" class="form-control content" placeholder="Treść artykułu"></textarea>
           
       
            <div class="action-buttons">
            <md-button type="cancel" class="md-primary md-raised" @click="cancel">Anuluj</md-button>
            <md-button type="submit" class="md-primary md-raised" @click="submit">Dodaj</md-button>
        </div>
    </div>
</template>

<script>
        import router from "@/router"
import axios from "axios"

    export default {
        data(){
            return{
                title: '',
                content: '',
            }
            
        },
        methods:{
            cancel(){
                this.title="",
                this.content=""
            },
               redirectToHomepage(){
                   router.push({path: '/'})
               },
           async submit(){
               const postUrl = "http://127.0.0.1:8000/api/articles/"
              await axios.post(postUrl, 
               {
                title: this.title,
                content: this.content,
               })
               this.redirectToHomepage()
            },
        }
    }
</script>

<style lang="scss" scoped>

.new-article-container{
    width: 80vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    
}

   .form-control{
    width: 80%;
    margin: 10px;
    padding: 10px;
    border: 2px solid grey;
    border-radius: 10px;
   }
   .title{
    height: 70px;
    font-size: 25px;
   }
   .content{
    height: 320px;
    font-size: 20px;
   }
    

.action-buttons{
    width: 80%;
    display: flex;
    justify-content: space-between;
   
}


</style>