<template>
  <div class="main">
    <h1>{{ title }}</h1>
    <div class="block">
    <h2> YOUTUBE LINKS </h2>
      <input class="text-input" 
        :value="songURL"
        @input="songURL = $event.target.value"
        placeholder= 'drop your favorite youtube song here'>
        <input class="text-input" 
        :value="cookingURL"
        @input="cookingURL = $event.target.value"
        placeholder= 'another link, maybe cooking ?'>
        <input class="text-input" 
        :value="otherURL"
        @input="otherURL = $event.target.value"
        placeholder= 'just drop another one here, anything you like'>
        </div>
      <div class="block">
       <h2> TEXTS </h2>
        <input 
        class="text-input" 
        :value="userData.name"
        @input="userData.name = $event.target.value" placeholder="your name">
        <input 
        class="text-input" 
        :value="userData.friend"
        @input="userData.friend = $event.target.value" placeholder="your best friend's name">
        <input 
        class="text-input" 
        :value="userData.mom"
        @input="userData.mom = $event.target.value" placeholder="your mom's name">
        <input 
        class="text-input" 
        :value="userData.pet"
        @input="userData.pet = $event.target.value" placeholder="your pet's name">
    </div>
    <button v-on:click="submitData">SEND TO DISCO CITY</button>
  </div>
</template>

</div>

<script>

  export default {
    data() {
      return {
        title: 'UNIciTY',
        songURL:'',
        cookingURL:'',
        otherURL:'',
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

