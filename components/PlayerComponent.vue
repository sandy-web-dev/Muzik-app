<template>
  <div class="player-section">
    <div class="iq-footer">
      <div class="row">
        <div class="col-sm col-12">
          <div class="player row " v-if="Object.keys($store.state.player.song).length > 0">
            <!--=============================================Song Name And Artist Name===========================================-->
            <div class="details col-12 col-sm-6 col-md-4 col-lg-4 ">
              <div class="track-art"></div>
              <div>
                <div class="track-name">{{ $store.state.player.song.song_name }}</div>
                <div class="track-artist">{{ $store.state.player.song.artists }}</div>
              </div>
            </div>
            <!--============================================Song Name And Artist Name Close =====================================-->

            <!--============================================ Previous Song Play Song Next Song ==================================-->
            <div class="buttons col-12 col-sm-3 col-md-2 col-lg-2">
              <audio
                ref="audioElement"
                :src="$store.state.player.song.song_file"
                @ended="nextSong"
                @timeupdate="updateCurrentTime">
              </audio>
              <div class="prev-track" @click="prevSong"><i class="fas fa-step-backward fa-2x"></i></div>
              <div style="cursor: pointer">
                <i class=" far fa-play-circle fa-3x text-white"
                   v-if="!$store.state.player.isPlaying"
                   @click="player"
                ></i>
                <i class="far fa-pause-circle fa-3x text-white"
                   @click="player"
                   v-else></i>
              </div>
              <div class="next-track"  @click="nextSong" ><i class="fas fa-step-forward fa-2x"></i></div>
            </div>
            <!--======================================== Previous Song Play Song Next Song Close ================================-->

            <!--======================================== Song Time And Duration =================================================-->
            <div class="slider_container slider_music col-12 col-sm-12 col-md-7 col-lg-5">
              <div class="current-time">{{calculateTime(currentTime)}}</div>
              <input
                type="range"
                min="0"
                :max="totalDurationSeconds"
                :value="currentTime"
                class="seek_slider"
                @change="seekTo"
              />
              <div class="total-duration">{{$store.state.player.song.song_details.formated_duration}}</div>
              <!--======================================== Song Time And Duration Close ===========================================-->
              <!--======================================== Audio Volume ===========================================================-->
              <div class="   col-sm-6 col-md-4 col-lg-4 d-flex align-items-center">
                <div class=" volume-icon">
                  <i class="fa fa-volume-up" @click="showVolume = !showVolume"></i>
                </div>
                <input
                  type="range"
                  min="0"
                  max="1"
                  step="0.1"
                  :value="$store.state.player.volume"
                  class="volume_slider"
                  v-show="showVolume"
                  @input="volumeChange"

                />
              </div>
              <!--======================================== Audio Volume Close =====================================================-->
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PlayerComponent",
  data(){
    return{
      isPlaying:false,
      totalDuration:"00:00",
      currentTime:0,
      totalDurationSeconds:0,
      showVolume:false,
    }
  },
  watch:{
    currentTime(seconds){
    },
  },
  mounted() {
    this.$store.dispatch('player/getSongs')
    this.$store.watch(state => {
      return state.player.isPlaying;
    }, (newValue)=>{
      const audioPlayer = this.$refs.audioElement;
      if(newValue){
        audioPlayer.play()
      }else{
        audioPlayer.pause()
      }
    })


    this.$store.watch(state => {
      return state.player.song;
    }, (newValue, oldValue)=>{
      if (Object.keys(oldValue).length === 0) return;
      this.player()
    })
  },

  methods:{
    //************************************************************************************* Audio Play Pause
    player(){
      const audioPlayer = this.$refs.audioElement;
      if(audioPlayer.paused){
        this.$store.dispatch("player/setPlayerState", true)
        audioPlayer.play();
      }else{
        this.$store.dispatch("player/setPlayerState", false)
        audioPlayer.pause();
      }
      this.currentTime = audioPlayer.currentTime
      this.totalDurationSeconds = this.$store.state.player.song.song_details.estimated_duration;
    },
    //************************************************************************************* Audio Play Pause Close
    //************************************************************************************* Volume Change
    volumeChange(e){
      const audioPlayer = this.$refs.audioElement;
      const volume =parseFloat(e.target.value)
      audioPlayer.volume =volume ;// 0.5
      this.$store.dispatch("player/setPlayerVolume", volume)
    },
    //************************************************************************************* Volume Change Close
    //************************************************************************************* Song Time Slider
    calculateTime(secs){
      const minutes = Math.floor(secs / 60);
      const seconds = Math.floor(secs % 60);
      const returnedSeconds = seconds < 10 ? `0${seconds}` : `${seconds}`;
      return `${minutes}:${returnedSeconds}`;
    },
    updateCurrentTime(){
      const audioPlayer = this.$refs.audioElement;
      this.currentTime = audioPlayer.currentTime
    },
    seekTo(e){
      const time = e.target.value;
      const audioPlayer = this.$refs.audioElement;
      audioPlayer.currentTime = time;
      this.currentTime = audioPlayer.currentTime
    },
    //************************************************************************************* Song Time Slider Close
    //************************************************************************************* Prev Song
    prevSong(){
      let value = this.$store.state.player.currentIndex
      const songs = this.$store.state.player.songs

      if(value === 0) return

      this.$store.dispatch(
        'player/setPlayerSong',
        {song:songs[value - 1], index:value-1}
      )
      this.$store.dispatch('player/setCurrentIndex', value-1)
    },
    //************************************************************************************ Prev Song Close
    //************************************************************************************ Next Song
    nextSong(){
      let value = this.$store.state.player.currentIndex
      const songs = this.$store.state.player.songs

      if((value + 1) === songs.length) return

      this.$store.dispatch(
        'player/setPlayerSong',
        {song:songs[value + 1], index:value+1}
      )
      this.$store.dispatch('player/setCurrentIndex', value+1)
    },
    //************************************************************************************** Next Song Close

  }
}
</script>

<style scoped>

</style>
