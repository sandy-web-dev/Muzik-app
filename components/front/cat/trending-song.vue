<template>
  <div class="overflow-hidden">
    <div class="row mt-md-3">
      <div class="col-lg-12">
        <div class="iq-card">
          <div class="iq-card-header">
            <div class="iq-header-title">
              <h4 class="card-title">Trending Songs</h4>
            </div>
            <div class="d-flex iq-view">
              <b class="text-primary">
                <nuxt-link to="/song-list" class="text-decoration-none">View More
                  <i class="fas fa-angle-right"></i>
                </nuxt-link>
              </b>
            </div>
          </div>
          <div class="iq-card-body">
            <div class="row">
              <div class="col-lg-2 col-md-3 col-sm-6 col-12 mb-2 iq-music-box"
                   v-for="i in 12"
                   :key="i"
                   aria-hidden="false">
                <div class="card">
                  <div class="iq-thumb">
                    <div class="iq-music-overlay"></div>
                    <nuxt-link to="single-song" >
                      <img src="/move%20like%20it.png" alt="" class="card-img-top">
                    </nuxt-link>
                    <nuxt-link to="single-song" class=" play-btn">
                      <i class="far fa-play-circle"></i>
                    </nuxt-link>
                  </div>
                  <div class="card-body text-center">
                    <nuxt-link to="/song-details">
                      Pop Smoke
                    </nuxt-link>
                    <p>
                      Justin Bieber
                    </p>
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
  name: "trending-song"
}
</script>

<style scoped>
.row{

}
.col-lg-12{
  padding-left: 15px;
  padding-right: 15px;
}
.col-lg-12 .iq-card-body {
  padding: 20px;
}
.iq-card{
  background: var(--iq-light-card);
  border-radius: 15px;
  margin-bottom: 30px;
  border: none;
  box-shadow: 0px 4px 20px 0px rgba(44, 101, 144, 0.1);
}
.iq-card-header{
  padding: 20px;
  align-items: center!important;
  border-bottom: 1px solid var(--iq-border-light);
  justify-content: space-between !important;
  display: flex;
}
.card-title{
  font-weight: 700;
}
.card{
  margin-bottom: 10px;
  border-top-right-radius: 15px;
  border-bottom-right-radius: 0px;
  border-bottom-left-radius: 15px;
}
.card img{
  border-top-left-radius: 0;
  border-top-right-radius: 15px;
  border-bottom-left-radius: 15px;
}

.card-body a{
  text-decoration: none;
  font-weight: 600;
  font-size: 1.400em;
  color: var(--iq-black);
}
.text-primary a{
  color: var(--iq-primary);
}
/*=================================CARD BOX================================*/
.iq-thumb{
  position: relative;
}
.iq-music-overlay {
  background: rgba(0, 0, 0, 0.7);
  position: absolute;
  height: 100%;
  width: 100%;
  left: 0;
  top: 0;
  bottom: 0;
  right: 0;
  opacity: 0;
  transition: all 0.4s ease-in-out 0s;
  border-radius: 0px 15px; }
.iq-thumb:hover .iq-music-overlay {
  opacity: 1;
}

.play-btn{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  visibility:  hidden;
  font-size: 40px;
  color:var(--iq-light);
  transition: all 0.1s ease-in-out 0.1s;
}
.iq-thumb:hover .play-btn{
  visibility: visible;
}

</style>
