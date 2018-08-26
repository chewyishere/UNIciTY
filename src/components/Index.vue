<template>
  <div class="main">
    <h1>{{ title }}</h1>
    <div class="block">
    <h2> {{ subtitle1 }} </h2>
      <input class="text-input" 
        :value="songURL"
        @input="songURL = $event.target.value" :placeholder="videoplaceholders[0]">
        <input class="text-input" 
        :value="cookingURL"
        @input="cookingURL = $event.target.value" :placeholder="videoplaceholders[1]">
        <input class="text-input" 
        :value="otherURL"
        @input="otherURL = $event.target.value" :placeholder="videoplaceholders[2]">
        </div>
      <div class="block">
       <h2>  {{ subtitle2 }} </h2>
        <input 
        class="text-input" 
        :value="userData.name"
        @input="userData.name = $event.target.value" :placeholder="nameplaceholders[0]">  
        <input 
        class="text-input" 
        :value="userData.friend"
        @input="userData.friend = $event.target.value" :placeholder="nameplaceholders[1]">
        <input 
        class="text-input" 
        :value="userData.mom"
        @input="userData.mom = $event.target.value" :placeholder="nameplaceholders[2]">
        <input 
        class="text-input" 
        :value="userData.pet"
        @input="userData.pet = $event.target.value" :placeholder="nameplaceholders[3]">
    </div>
    <button v-on:click="submitData">Send to Unity</button>
  </div>
</template>

</div>

<script>
import data from '../json/data.json';

  export default {

    data() {
      return {
        content: data,
        title: data.contents.Title,
        subtitle1: data.contents.VideoTitle,
        subtitle2: data.contents.NameTitle,
        videoplaceholders: data.contents.VideoInputPlaceholders,
        nameplaceholders: data.contents.NameInputPlaceholders,
        songURL:'',
        cookingURL:'',
        otherURL:'',
        btnSend: data.contents.BtnSend,
        userData: {
          songID: '',
          cookingID:'',
          otherID:'',
          name: '',
          friend:'',
          mom:'',
          pet:'',
        },
      }
    },
    methods: {
      parseYoutube(url){
          var regExp = /^.*((youtu.be\/)|(v\/)|(\/u\/\w\/)|(embed\/)|(watch\?))\??v?=?([^#\&\?]*).*/;
          var match = url.match(regExp);
          return (match&&match[7].length==11)? match[7] : false;
      },

      submitData() { 
         this.userData.songID = this.parseYoutube(this.songURL);
         this.userData.cookingID = this.parseYoutube(this.cookingURL);
         this.userData.otherID = this.parseYoutube(this.otherURL);

         console.log(this.userData);

         this.$http.put('https://ardiscocity.firebaseio.com/data.json', this.userData)
         .then(response => {


          console.log(response);
        }, error => {
          console.log(error);
        });
      }
    }
  }
</script>

