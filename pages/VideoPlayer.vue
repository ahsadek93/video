<template>
  <div class="container-fluid bg-secondary container-height" id="app">
    <div class="row justify-content-center h-100">
      <div class="col-12 col-md-10 col-lg-8 px-0 d-flex">
        <div class="row mx-0 align-self-center justify-content-center w-100">


          <div class="videoWrapper py-md-0 col-12 col-sm-8 col-md-6 col-lg-5 d-flex px-0">

            <video ref="myvideo" autoplay muted loop id="myvideo" class="video">
              <source
                src="https://d3nw8wgk2sd2ed.cloudfront.net/_ijU9sOPp.mp4"
              />
              <track src="https://genwin.app/web/videos/static/_ijU9sOPp.vtt" kind="captions"  label="English" default="default" />
            </video>

            <div class="content py-md-0 d-flex flex-column" @click="playPause">
              <div class="row mx-0 justify-content-center">
                <div class="col-12 mt-3">
                  <a href="#" class="text-white"
                    ><i class="fa fa-2x fa-arrow-left"></i
                  ></a>
                </div>
              </div>
              <div class="row mx-0 justify-content-center pt-5 pt-md-3">
                <div v-if="isClicked" class="col-11 col-md-8 progressWrapper">
                  <span class="text-danger text-small">$15000</span>
                  <div class="progress">
                    <div
                      class="progress-bar bg-danger w-75"
                      role="progressbar"
                      aria-valuenow="75"
                      aria-valuemin="0"
                      aria-valuemax="100"
                    ></div>
                  </div>
                  <div class="text-white bg-semi">
                    <p class="m-0">Dress for the cause challenge</p>
                    <p class="m-0 text-danger">
                      Breast Cancer society of Canada
                    </p>
                  </div>
                </div>
              </div>
              <div class="row mx-0 justify-content-center flex-grow-1">
                <div
                  v-if="!isPlaying"
                  class="col-12 align-self-center text-center bg-semi"
                >
                  <span class="text-white">
                    <i class="far fa-2x fa-play-circle"></i
                  ></span>
                </div>
              </div>
              <div
                class="row mx-0 justify-content-center flex-grow-2 py-5 py-md-3"
              >
                <div
                  v-if="isVisible"
                  class="col-10 d-flex justify-content-center text-center rounded"
                >
                  <p class="m-0 text-white align-self-center bg-semi">
                    It was time for me to challenge this
                  </p>
                </div>
              </div>
              <div class="row mx-0 justify-content-center">
                <div
                  v-if="isClicked"
                  class="col-12 d-flex justify-content-center text-center rounded py-3"
                >
                  <div class="row justify-content-center w-100">
                    <div class="col-12 col-sm-5 col-md-10 p-0">
                      <div class="row w-100 justify-content-between m-0">
                        <div
                          class="col-4 text-center text-danger text-small border-right"
                        >
                          <span>By</span>
                        </div>
                        <div
                          class="col-4 text-center text-danger text-small border-right"
                        >
                          Raised
                        </div>
                        <div class="col-4 text-center text-danger text-small">
                          <i class="fas fa-heart"></i>
                        </div>
                        <div
                          class="col-4 text-center text-white text-small border-right"
                        >
                          <span>Ann Smith</span>
                        </div>
                        <div
                          class="col-4 text-center text-white text-small border-right"
                        >
                          $15K
                        </div>
                        <div class="col-4 text-center text-white text-small">
                          456K
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="row mx-0 justify-content-center">
                <div class="col-12">
                  <div class="row justify-content-between">
                    <div class="text-white text-center py-2 px-0 col-4">
                      <a href="#" class="text-white">
                        <i class="fa fa-info-circle"></i>
                        <span class="d-block text-small">Information</span></a
                      >
                    </div>
                    <div class="text-white text-center py-3 px-0 col-4">
                      <a
                        href="#"
                        class="btn btn-outline-danger text-small align-self-center text-white rounded"
                        ><i class="fas fa-video mr-1"></i>DRESS UP</a
                      >
                    </div>
                    <div class="text-white text-center py-2 px-0 col-4">
                      <a href="#" class="text-white"
                        ><i class="fas fa-hand-holding-heart"></i>
                        <span class="d-block text-small">Sponser Me</span></a
                      >
                    </div>
                  </div>
                </div>
              </div>
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
