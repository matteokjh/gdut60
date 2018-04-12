<template>
  <div class="hello">
  	<div v-for=" (e, idx) in List">
	  <div :class="['a'+idx, 'box']" :style="{'background-image': 'url('+e.bgUrl+')', 'background-position': '50%'+ bgTop + 'px'}">
	  	<p>这里是{{ e.time }}</p>
		<div class="left" :style="{'margin-top': top + 'px'}">
			<img v-for="k in e.lImg" :src="k" alt="">
		</div>
		<div class="right" :style="{'margin-top': top + 'px'}">
			<img  v-for="k in e.rImg" :src="k" alt="">
		</div>
	  </div>
	</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
	return {
	  List: [
		  {
			  time: '2018',
			  bgUrl: '/static/bg1.png',
			  lImg: [
				  '/static/ec1.png',
				  '/static/w1.png',
				  '/static/ec3.png',
				  '/static/ec4.png',
				  '/static/ec5.jpg',
				  '/static/s1.jpg',
				  '/static/s2.jpg',
			  ],
			  rImg: [
				  '/static/ec6.png',
				  '/static/s1.png',
				  '/static/w2.png',
				  '/static/s3.jpg',
				  '/static/shiki.jpg',
				  '/static/r1.jpg',
				  '/static/r2.png'
			  ]
		  },{
			  time: '2010',
			  bgUrl: '/static/bg2.png',
			  lImg: [
				  '/static/ec1.png',
				  '/static/w1.png',
				  '/static/ec3.png',
				  '/static/ec4.png',
				  '/static/ec5.jpg',
				  '/static/s1.jpg',
				  '/static/s2.jpg',
			  ],
			  rImg: [
				  '/static/ec6.png',
				  '/static/s1.png',
				  '/static/w2.png',
				  '/static/s3.jpg',
				  '/static/shiki.jpg',
				  '/static/r1.jpg',
				  '/static/r2.png'
			  ]
		  },{
			  time: '2005',
			  bgUrl: '/static/bg3.png',
			  lImg: [
				  '/static/ec1.png',
				  '/static/w1.png',
				  '/static/ec3.png',
				  '/static/ec4.png',
				  '/static/ec5.jpg',
				  '/static/s1.jpg',
				  '/static/s2.jpg',
			  ],
			  rImg: [
				  '/static/ec6.png',
				  '/static/s1.png',
				  '/static/w2.png',
				  '/static/s3.jpg',
				  '/static/shiki.jpg',
				  '/static/r1.jpg',
				  '/static/r2.png'
			  ]
		  },{
			  time: '2000',
			  bgUrl: '/static/bg4.png',
			  lImg: [
				  '/static/ec1.png',
				  '/static/w1.png',
				  '/static/ec3.png',
				  '/static/ec4.png',
				  '/static/ec5.jpg',
				  '/static/s1.jpg',
				  '/static/s2.jpg',
			  ],
			  rImg: [
				  '/static/ec6.png',
				  '/static/s1.png',
				  '/static/w2.png',
				  '/static/s3.jpg',
				  '/static/shiki.jpg',
				  '/static/r1.jpg',
				  '/static/r2.png'
			  ]
		  },{
			  time: '1958',
			  bgUrl: '/static/bg5.png',
			  lImg: [
				  '/static/ec1.png',
				  '/static/w1.png',
				  '/static/ec3.png',
				  '/static/ec4.png',
				  '/static/ec5.jpg',
				  '/static/s1.jpg',
				  '/static/s2.jpg',
			  ],
			  rImg: [
				  '/static/ec6.png',
				  '/static/s1.png',
				  '/static/w2.png',
				  '/static/s3.jpg',
				  '/static/shiki.jpg',
				  '/static/r1.jpg',
				  '/static/r2.png'
			  ]
		  },
	  ],
	  top: 0,
	  bgTop: 0
	}
  },
  methods: {
	  slider() {
		  let cHeight = document.documentElement.clientHeight;
		  let height = document.documentElement.scrollHeight;
		  let scroll = document.documentElement.scrollTop;
		  console.log(scroll + cHeight !== height)
		  if(scroll + cHeight !== height){
			this.top = -scroll/5;
		  	this.bgTop = -scroll/20;
		  }
	  }
  },
  mounted() {
	window.addEventListener('scroll', this.slider)
  }
}
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
.box {
	border: .2px solid white;
	height: 100%;
	overflow: hidden;
	width: 100%;
	background-size: 150%;
	background-repeat: no-repeat;
	transition: all .6s ease;
}
.right {
	display: inline-block;
	width: 30%;
	transition: all .6s ease;
}
.a4 .left {
	vertical-align: baseline;
}
.left {
	vertical-align: top;
	display: inline-block;
	width: 40%;
	transition: all .6s ease;
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
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
