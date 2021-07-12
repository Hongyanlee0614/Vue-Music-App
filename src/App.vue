<template>
  <header>
    <h1>我要我们在一起音乐歌单</h1>
  </header>
  <main>
    <section class="player">
      <h2 class="song-title">
        {{ current.title }} - <span>{{ current.artist }}</span>
      </h2>
      <div class="controls">
        <button class="prev" @click="prev">Prev</button>
        <button class="play" v-if="!isPlaying" @click="play">Play</button>
        <button class="pause" v-else @click="pause">Pause</button>
        <button class="next" @click="next">Next</button>
      </div>
    </section>
    <br />
    <section class="playlist">
      <h3>音乐列表</h3>
      <button
        v-for="song in songs"
        :key="song.src"
        @click="play(song)"
        :class="song.src == current.src ? 'song playing' : 'song'"
      >
        {{ song.title }} - {{ song.artist }}
      </button>
    </section>
    <small class="author">2021 @angelol2046</small>
  </main>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {
          title:
            "這世界那麼多人（《我要我們在一起》電影主題曲）♫【無損高音質】",
          artist: "莫文蔚 Karen Mok",
          src: require("./assets/莫文蔚（Karen Mok） - 這世界那麼多人（《我要我們在一起》電影主題曲）♫【無損高音質｜CC歌詞字幕】（Music 2021）.mp3"),
        },
        {
          title:
            "不捨（電影《我要我們在一起》推廣曲）『我們都不配擁有另一個自我，分開比依偎的思念更執著。』",
          artist: "顏人中",
          src: require("./assets/顏人中 - 不捨（電影《我要我們在一起》推廣曲）『我們都不配擁有另一個自我，分開比依偎的思念更執著。』【動態歌詞Lyrics】.mp3"),
        },
        {
          title: "凌一尧，我亲爱的姑娘",
          artist: "彭飞",
          src: require("./assets/凌一尧，我亲爱的姑娘 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "我是你的",
          artist: "彭飞",
          src: require("./assets/我是你的 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "海岸线",
          artist: "彭飞",
          src: require("./assets/海岸线 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "窗外的风景",
          artist: "彭飞",
          src: require("./assets/窗外的风景 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "我要娶你为妻",
          artist: "彭飞",
          src: require("./assets/我要娶你为妻 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "雨夜",
          artist: "彭飞",
          src: require("./assets/雨夜 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "Take Me To Your Home",
          artist: "彭飞",
          src: require("./assets/Take Me To Your Home (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "第1854天",
          artist: "彭飞",
          src: require("./assets/第1854天 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "吕钦扬，我爱你",
          artist: "彭飞",
          src: require("./assets/吕钦扬，我爱你 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "浇筑",
          artist: "彭飞",
          src: require("./assets/浇筑 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "最好的生活",
          artist: "彭飞",
          src: require("./assets/最好的生活 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "吕工",
          artist: "彭飞",
          src: require("./assets/吕工 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "别告诉凌一尧i",
          artist: "彭飞",
          src: require("./assets/别告诉凌一尧i (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "你还爱我么",
          artist: "彭飞",
          src: require("./assets/你还爱我么 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "这么多年了，我都替你不值",
          artist: "彭飞",
          src: require("./assets/这么多年了，我都替你不值 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "我想见你",
          artist: "彭飞",
          src: require("./assets/我想见你 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "各自奔赴的爱情",
          artist: "彭飞",
          src: require("./assets/各自奔赴的爱情 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "你是不是该娶我了",
          artist: "彭飞",
          src: require("./assets/你是不是该娶我了 (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "别告诉凌一尧ii",
          artist: "彭飞",
          src: require("./assets/别告诉凌一尧ii (电影《我要我们在一起》配乐).mp3"),
        },
        {
          title: "《這世界那麼多人 Empty World》- 電影「我要我們在一起」主題曲",
          artist: "莫文蔚 Karen Mok",
          src: require("./assets/莫文蔚 Karen Mok《這世界那麼多人 Empty World》Official MV - 電影「我要我們在一起」主題曲.mp3"),
        },
      ],
      player: new Audio(),
    };
  },
  methods: {
    play(song) {
      if (typeof song.src != "undefined") {
        this.current = song;
        this.player.src = this.current.src;
      }
      this.index = this.songs.indexOf(this.current);
      this.player.play();
      this.player.addEventListener(
        "ended",
        function() {
          this.index++;
          if (this.index > this.songs.length - 1) {
            this.index = 0;
          }
          this.current = this.songs[this.index];
          this.play(this.current);
        }.bind(this)
      );
      this.isPlaying = true;
    },
    pause() {
      this.player.pause();
      this.isPlaying = false;
    },
    next() {
      this.index++;
      if (this.index > this.songs.length - 1) {
        this.index = 0;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },
    prev() {
      this.index--;
      if (this.index < 0) {
        this.index = this.songs.length - 1;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },
  },
  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: sans-serif;
}
header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
  background-color: #212121;
  color: #ffffaa;
}
main {
  width: 100%;
  max-width: 2330px;
  margin: 0 auto;
  padding: 20px;
  background-image: url(./assets/image.jpg);
  background-size: auto 100%;
  background-position: -170px 0;
  text-align: center;
}
main:after {
  opacity: 0.1;
}
.song-title {
  color: white;
  font-size: 32px;
  font-weight: 700;
  text-transform: uppercase;
  text-align: center;
}
.song-title span {
  font-weight: 400;
  font-style: italic;
}
.controls {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 30px 15px;
}
button {
  appearance: none;
  background: none;
  border: none;
  outline: none;
  cursor: pointer;
}
button:hover {
  opacity: 0.8;
}
.play,
.pause {
  font-size: 20px;
  font-weight: 700;
  padding: 15px 25px;
  margin: 0px 15px;
  border-radius: 8px;
  color: #fff;
  background-color: #cc2e5d;
}
.next,
.prev {
  font-size: 16px;
  font-weight: 700;
  padding: 10px 20px;
  margin: 0px 15px;
  border-radius: 6px;
  color: #fff;
  background-color: #ff5858;
}
.playlist {
  padding: 0px 30px;
}
.playlist h3 {
  color: #ffffaa;
  font-size: 28px;
  font-weight: 400;
  margin-top: 10px;
  margin-bottom: 30px;
  text-align: center;
}
.playlist .song {
  display: block;
  width: 100%;
  padding: 15px;
  font-size: 20px;
  font-weight: 700;
  cursor: pointer;
  color: #ffffee;
}
.playlist .song:hover {
  color: #ff5858;
}
.playlist .song.playing {
  color: #fff;
  background-image: linear-gradient(to right, #cc2e5d, #ff5858);
}
.author {
  text-align: center;
  opacity: 0.7;
}
</style>
