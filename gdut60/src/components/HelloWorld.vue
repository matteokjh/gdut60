<template>
  	<div>

  		<div v-for=" (e, idx) in List">
				<div :class="['a'+idx, 'box']" :style="{'background-image': 'url('+e.bgUrl+')', 'background-position': '50%'+ bgTop + 'px'}">
					<p>这里是{{ e.time }}</p>

					<div class="left" :style="{'margin-top': top + 'px'}" >
						<img v-for="k in e.lImg" :src="k" alt="" @click="clickImg($event)">
					</div>

					<div class="right" :style="{'margin-top': top + 'px'}">
						<img  v-for="k in e.rImg" :src="k" alt="" @click="clickImg($event)">
					</div>
				</div>
	 		</div>
		 
			<div id="myModal" class="modal">
				<img :src="imgSrc" class="modal-content" @click="closeModal()">
			</div>

  	</div>
</template>

<script>
export default {
  data() {
    return {
      List: [
        {
          time: "2018",
          bgUrl: "/static/bg1.png",
          lImg: [
            "/static/ec1.png",
            "/static/w1.png",
            "/static/ec3.png",
            "/static/ec4.png",
            "/static/ec5.jpg",
            "/static/s1.jpg",
            "/static/s2.jpg"
          ],
          rImg: [
            "/static/ec6.png",
            "/static/s1.png",
            "/static/w2.png",
            "/static/s3.jpg",
            "/static/shiki.jpg",
            "/static/r1.jpg",
            "/static/r2.png"
          ]
        },
        {
          time: "2010",
          bgUrl: "/static/bg2.png",
          lImg: [
            "/static/ec1.png",
            "/static/w1.png",
            "/static/ec3.png",
            "/static/ec4.png",
            "/static/ec5.jpg",
            "/static/s1.jpg",
            "/static/s2.jpg"
          ],
          rImg: [
            "/static/ec6.png",
            "/static/s1.png",
            "/static/w2.png",
            "/static/s3.jpg",
            "/static/shiki.jpg",
            "/static/r1.jpg",
            "/static/r2.png"
          ]
        },
        {
          time: "2005",
          bgUrl: "/static/bg3.png",
          lImg: [
            "/static/ec1.png",
            "/static/w1.png",
            "/static/ec3.png",
            "/static/ec4.png",
            "/static/ec5.jpg",
            "/static/s1.jpg",
            "/static/s2.jpg"
          ],
          rImg: [
            "/static/ec6.png",
            "/static/s1.png",
            "/static/w2.png",
            "/static/s3.jpg",
            "/static/shiki.jpg",
            "/static/r1.jpg",
            "/static/r2.png"
          ]
        },
        {
          time: "2000",
          bgUrl: "/static/bg4.png",
          lImg: [
            "/static/ec1.png",
            "/static/w1.png",
            "/static/ec3.png",
            "/static/ec4.png",
            "/static/ec5.jpg",
            "/static/s1.jpg",
            "/static/s2.jpg"
          ],
          rImg: [
            "/static/ec6.png",
            "/static/s1.png",
            "/static/w2.png",
            "/static/s3.jpg",
            "/static/shiki.jpg",
            "/static/r1.jpg",
            "/static/r2.png"
          ]
        },
        {
          time: "1958",
          bgUrl: "/static/bg5.png",
          lImg: [
            "/static/ec1.png",
            "/static/w1.png",
            "/static/ec3.png",
            "/static/ec4.png",
            "/static/ec5.jpg",
            "/static/s1.jpg",
            "/static/s2.jpg"
          ],
          rImg: [
            "/static/ec6.png",
            "/static/s1.png",
            "/static/w2.png",
            "/static/s3.jpg",
            "/static/shiki.jpg",
            "/static/r1.jpg",
            "/static/r2.png"
          ]
        }
      ],
      top: 0,
      bgTop: 0,
      imgSrc: ""
    };
  },
  methods: {
    slider() {
      let cHeight = document.documentElement.clientHeight;
      let height = document.documentElement.scrollHeight;
      let scroll = document.documentElement.scrollTop;
      if (scroll + cHeight !== height) {
        this.top = -scroll / 5;
        this.bgTop = -scroll / 20;
      }
    },
    clickImg(e) {
      var modal = document.getElementById("myModal");
      modal.style.display = "block";
      this.imgSrc = e.currentTarget.src;
    },
    closeModal(e) {
      var modal = document.getElementById("myModal");
      modal.style.display = "none";
    }
  },
  mounted() {
    window.addEventListener("scroll", this.slider);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
  padding: 0;
}
body {
  max-width: 600px;
}

html,
body {
  height: 100%;
  overflow: hidden;
}

.modal {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: hidden; /* Enable scroll if needed */
  background-color: rgb(0, 0, 0); /* Fallback color */
  background-color: rgba(0, 0, 0, 0.9); /* Black w/ opacity */
}

.modal-content {
  margin: auto;
  display: block;
  overflow: auto;
  animation-name: zoom;
  animation-duration: 0.6s;
}

@keyframes zoom {
  from {
    transform: scale(0);
  }
  to {
    transform: scale(1);
  }
}

.box {
  border: 0.2px solid white;
  height: 100%;
  width: 100%;
  background-size: 150%;
  background-repeat: no-repeat;
  transition: all 0.6s ease;
}

.right {
  display: inline-block;
  width: 30%;
  transition: all 0.6s ease;
}

.a4 .left {
  vertical-align: baseline;
}
.left {
  vertical-align: top;
  display: inline-block;
  width: 40%;
  transition: all 0.6s ease;
}

.left img:hover {
  background: rgba(25, 55, 255, 0.7);
  z-index: 999;
}

.left img {
  width: 100%;
}

.right img {
  width: 100%;
}

p {
  color: white;
}

a {
  color: #42b983;
}
</style>
