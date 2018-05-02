<template>
	<div class="hello" :style="{'background-image': 'url('+bgUrl+')','margin-top': top + 'px','background-size': 'cover','background-repeat': 'no-repeat'}">
		<img src="/static/main.png" class="main">
		<div v-for=" (e, idx) in List" :class="['a'+idx, 'box']">
			<div class="text">
				<div :class="a.year" v-for="a in e.text">
					<p v-for="b in a.info" >
						{{ b }}
					</p>
				</div>
			</div>
			<div class="surface">
				<div class="left">
					<img v-for="k in e.lImg.surface" :src="k" alt="">
				</div>
				<div class="right">
					<img  v-for="k in e.rImg.surface" :src="k" alt="">
				</div>
			</div>
			<div class="bottom">
				<div class="left">
					<img v-for="k in e.lImg.bottom" :src="k" alt="">
				</div>
				<div class="right">
					<img  v-for="k in e.rImg.bottom" :src="k" alt="">
				</div>
			</div>
		</div>
	</div>

  	<div>

  		<div v-for=" (e, idx) in List">

						 
				<div id="myModal" class="modal"  @click="closeModal()">
					<img :src="imgSrc" class="modal-content">
				</div>

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


  	</div>
</template>

<script>
export default {
	name: 'HelloWorld',
	data () {
		return {
			List: [
				{ //////////////////     第一块       ///////////////////
					text: [
						{
							year: '1958',
							info: [
								'建校于1958年',
								'最初，校名为',
								'广州工学院'
							]
						},{
							year: '1962',
							info: [
								'1962年改名为',
								'广东工学院'
							]
						},{
							year: '1995',
							info: [
								'1995年',
								'广东工学院',
								'广东机械学院',
								'华南建设学院(东院)',
								'合并为',
								'广东工业大学'
							]
						}
					],
					lImg: {
						bottom: [
							'/static/1/l1.jpg',
							'/static/1/l2.jpg',
							'/static/1/l3.jpg'
						],
						surface: [
							'/static/1/l4.jpg'
						]
					},
					rImg: {
						bottom: [
							'/static/1/r1.jpg',
							'/static/1/r2.jpg',
							'/static/1/r3.jpg',
							'/static/1/r4.jpg'
						],
						surface: [
							'/static/1/r5.jpg',
							'/static/1/r6.jpg'
						]
					}
				},{ //////////////////     第二块       ///////////////////
					text: [
						{
							year: '2008a',
							info: [
								'2008年',
								'广东工业大学',
								'成为广东省 “211工程”',
								'重点建设高校'
							]
						},{
							year: '2008b',
							info: [
								'2008年',
								'广东工业大学',
								'与东莞市人民政府共建',
								'广东华南工业设计院'
							]
						},{
							year: '2012',
							info: [
								'2012年',
								'广东工业大学工程学学科',
								'进入国际ESI',
								'位居世界排名前1%'
							]
						},{
							year: '2014',
							info: [
								'2014年',
								'广东工业大学全部专业',
								'纳入本科一批次招生'
							]
						},{
							year: '2015a',
							info: [
								'2015年',
								'广东工业大学成为',
								'广东高水平大学重点建设高校'
							]
						}
					],
					lImg: {
						bottom: [
							'/static/2/l1.jpg',
							'/static/2/l2.jpg'
						]

					},
					rImg: {
						bottom: [
							'/static/2/r1.jpg',
							'/static/2/r2.jpg'
						]
					}
				},{//////////////////     第三块       ///////////////////
					text: [
						{
							year: '2015b',
							info: [
								'2015年',
								'广东工业大学与香港科技大学联合承办',
								'第十四届“挑战杯”全国大学生课外学术科技作品竞赛'
							]
						},{
							year: '2017a',
							info: [
								'2017年',
								'广东工业大学入选',
								'教育部全国首批',
								'“深化创新创业教育改革示范高校”'
							]
						}
						
					],
					lImg: {
						bottom: [
							'/static/3/l1.jpg'
						],
						surface: [
							'/static/3/l2.jpg'
						]
					},
					rImg: {
						surface: [
							'/static/3/r1.jpg'
						]
					}
				},{//////////////////     第四块       ///////////////////
					text: [
						{
							year: '2017b',
							info: [
								'2017年',
								'广东工业大学',
								'入选“全国大学生创业示范园”'
							]
						},
						{
							year: '2018a',
							info: [
								'2018年',
								'广东工业大学获教育部首批',
								'“新工科”研究与实践项目'
							]
						},
						{
							year: '2018b',
							info: [
								'2018年',
								'广东工业大学成为',
								'“粤港澳大湾区发展广州智库”',
								'核心成员机构'
							]
						}
					],
					lImg: {
						bottom: [
							'/static/4/l1.png',
							'/static/4/l2.jpg',
							'/static/4/l3.jpg'
						]
					},
					rImg: {
						bottom: [
							'/static/4/r1.jpg',
							'/static/4/r2.png',
							'/static/4/r4.jpg'
						],
						surface: [
							'/static/4/r3.png',
							'/static/4/r5.png'
						]
					}
			}
			],
			top: 0,
			bgTop: 0,
			bgUrl: '/static/BG.png'
		}
	},
	methods: {
		slider() {
			let cHeight = document.documentElement.clientHeight;
			let height = document.documentElement.scrollHeight;
			let scroll = document.documentElement.scrollTop;
			console.log(scroll + cHeight !== height)
			if(scroll + cHeight !== height){
				this.top = -scroll/20;
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
@font-face {
	font-family: fzxk;
	src: url('/static/方正行楷_GBK.ttf')
}
.main {
	position: absolute;
    width: 35%;
    z-index: 3;
    left: 0;
    top: 0;
    right: 0;
    bottom: 40%;
    margin: auto;
}
.text {
	position: absolute;
	z-index: 3;
}
.text p {
	font-size: 1.5rem;
	text-shadow: 3px 4px 2px black;
}
.modal {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
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
	position: relative;
	height: 100%;
	width: 100%;
	background-size: 100%;
	background-repeat: no-repeat;
	transition: all .6s ease;
}
.surface {
	position: absolute;
	z-index: 2;
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
	width: 30%;
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
	font-family: 'fzxk';
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
