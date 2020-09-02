<template>

  <div class="container-fluid bg-secondary container-height" id="app">
    <div class="row justify-content-center h-100">
      <div class="col-12 col-md-10 col-lg-8 px-0 d-flex">
        <div class="row mx-0 align-self-center justify-content-center w-100">
          <div class="videoWrapper py-md-0 col-12 col-sm-8 col-md-6 col-lg-5 px-0">
              <div class="row justify-content-center">
                   <vue-record-video />
              </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>



export default {

  

  data() {
    return {
      isPlaying: true,
      isClicked: false,
      isVisible: true,
    }
  },

  mounted() {
    setTimeout(() => {
      //this.$refs.myvideo.pause();
      //this.$refs.myvideo.muted = !this.$refs.myvideo.muted;
      if (this.isPlaying) {
        this.isVisible = false
      } else {
        this.isVisible = true
      }
    }, 3000)
  },

  methods: {
    playPause() {
      if (this.isPlaying) {
        this.$refs.myvideo.pause()
        this.isPlaying = false
        this.isClicked = true
        this.isVisible = true
      } else {
        this.$refs.myvideo.play()
        this.isPlaying = true
        this.isClicked = false
        this.$refs.myvideo.muted = false
        this.checkVideoStates()
      }
    },

    checkVideoStates() {
      setTimeout(() => {
        if (this.isPlaying) {
          this.isVisible = false
        } else {
          this.isVisible = true
        }
      }, 3000)
    },
  },
}
</script>

<style lang="scss">

.container-height {
  height: 100vh;
  font-family: 'Montserrat', sans-serif;
}

.videoWrapper {
  position: relative;
  height: 100vh;

@media (min-width: 768px) { 
    
    height: 100%;
    max-height: 100vh;
 }


}

.video {
  object-fit:cover;
  width: 100%;
}

.content {
  position: absolute;
  width: 100%;
  height: 100%;
  cursor: pointer;
  top: 0;
}

.text-small {
  font-size: 0.77rem;
}

.rounded {
  border-radius: 1rem !important;
}

.bg-semi {
  background: rgba(0, 0, 0, 0.5);
  font-family: 'Montserrat', sans-serif;
}

.progress {
  height: 0.2rem;
}

.progressWrapper {
  font-family: 'Montserrat', sans-serif;
}



video::cue {
  background: rgba(0, 0, 0, 0.5);
}
</style>

</template>

<script>
export default {

}
</script>

<style>

</style>