<template>
    <v-ons-page>
      <v-ons-toolbar>
        <div class="center">{{ title }}</div>
        <div class="right">
          <v-ons-toolbar-button>
            <v-ons-icon icon="ion-navicon, material: md-menu"></v-ons-icon>
          </v-ons-toolbar-button>
        </div>
      </v-ons-toolbar>

      <v-ons-card>
        <img v-bind:src="image" style="width: 100%">
        
        <v-ons-list>
          <v-ons-list-item>
            <div class="left">
              種類
            </div>
            <div class="center">
              {{ name }}
            </div>
          </v-ons-list-item>
          <v-ons-list-item>
            <div class="left">
              説明
            </div>
            <div class="center">
              {{ description }}
            </div>
          </v-ons-list-item>
          <v-ons-list-item>
            <div class="left">
              鳴き声
            </div>
            <div class="center">
              <audio v-bind:src="sound" controls></audio>
            </div>
          </v-ons-list-item>
        </v-ons-list>
        
        <div style="text-align:center">
          <v-ons-button v-on:click="go_prev" style="margin: 6px 0"><v-ons-icon icon="md-caret-left"></v-ons-icon></v-ons-button>
          <v-ons-button v-on:click="go_next" style="margin: 6px 0"><v-ons-icon icon="md-caret-right"></v-ons-icon></v-ons-button>
        </div>

      </v-ons-card>

    </v-ons-page>
</template>
<script>

  const animals = [
    {
      image: "images/dog.png",
      name: "イヌ",
      description: "哺乳綱食肉目イヌ科に属する動物",
      sound: "sounds/dog.mp3"
    },
    {
      image: "images/cat.png",
      name: "ネコ",
      description: "食肉目ネコ科の哺乳類",
      sound: "sounds/cat.mp3"
    }
  ];

  export default{
    data() {
      return {
        title: "アルバム",
        index: 0,
        image: animals[0].image,
        name: animals[0].name,
        description: animals[0].description,
        sound: animals[0].sound
      };
    },
    methods: {
      go_next(){
        this.index += 1;
        this.image = animals[this.index].image;
        this.name = animals[this.index].name;
        this.description = animals[this.index].description;
        this.sound = animals[this.index].sound;
      },
        go_prev(){
        this.index -= 1;
        this.image = animals[this.index].image;
        this.name = animals[this.index].name;
        this.description = animals[this.index].description;
        this.sound = animals[this.index].sound;
      },     
    }
  };
</script>
