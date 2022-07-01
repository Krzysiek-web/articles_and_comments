<template>
    <div class="containerInput">
        
            <div class="form-group">
                <label for="nickname">Nickname</label>
                <input id="nickname" v-model="nickname" type="text" class="nickname" placeholder="Podaj swój nick" />
            </div>
            <div class="form-group">
                <textarea  v-model="content" name="textarea" rows="20" cols="100"></textarea>
            </div>
            <div class="action-button">
                <md-button type="cancel" class="md-primary" @click="cancel">Anuluj</md-button>
                <md-button type="submit" class="md-primary" @click="onCreateComment">Zapisz</md-button>
                
            </div>
        
    </div>
</template>

<script>
import axios from 'axios';

export default {
    props: {
    id: {
      type: [Number, String],
      required: true,
    },
  },
   data(){
    return{
        showDialog: false,
            nickname:'',
            content:'',
            
        
        
    }
   },
   methods:{
    cancel(){
        this.$emit('cancel', false);
    },
    async onCreateComment(){
        const postUrl = "http://127.0.0.1:8000/api/comments/"
       await axios.post(postUrl,
        {
            nickname: this.nickname,
            content: this.content,
            article: this.id,
        })
        this.cancel();
    },  
    
   
}}

</script>

<style lang="scss">
.containerInput{
    padding: 2em;
    display: flex;
    flex-direction: column;
}
.nickname{
margin: 10px;
padding: 10px;
}
.action-button{ 
    display: flex;
    justify-content: end;
}
</style>