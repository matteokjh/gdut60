<template>
<div style="position: relative;">
	<div class="hello" :style="{'background-attachment':'fixed','background-image': 'url('+bgUrl+')','background-size': 'cover','background-repeat': 'no-repeat'}">
		<img src="http://ots4cfy06.bkt.clouddn.com/0/main.png" class="main" :style="{'transition': 'all .5s ease','transform': 'translateY('+top*4+'%)','pointer-events':'none'}">
		<div v-for=" (e, idx) in List" :class="['a'+idx, 'box']">
			<div class="text" :style="{'margin-top': top*2 +'%'}">
				<div :class="'y-'+a.year" v-for="a in e.text">
					<p v-for="b in a.info" >
						{{ b }}
					</p>
				</div>
			</div>
			<div class="surface" :style="{'top': top*1.5 +'%'}">
				<div class="left">
					<img v-for="k in e.lImg.surface" :src="k" alt="" @click="clickImg($event)">
				</div>
				<div class="right">
					<img  v-for="k in e.rImg.surface" :src="k" alt="" @click="clickImg($event)">
				</div>
			</div>
			<div class="bottom" :style="{'transform': 'translateY('+ top +'%)'}">
				<div class="left">
					<img v-for="k in e.lImg.bottom" :src="k" alt="" @click="clickImg($event)">
				</div>
				<div class="right">
					<img  v-for="k in e.rImg.bottom" :src="k" alt="" @click="clickImg($event)">
				</div>
			</div>
		</div>

        <div id="myModal" class="modal"  @click="closeModal()" @mousemove="mouse($event)">
            <img :src="imgSrc" class="modal-content" id="coords">
        </div>
	</div>
    <img src="http://ots4cfy06.bkt.clouddn.com/0/main.png" class="footer">
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
							'http://ots4cfy06.bkt.clouddn.com/1/l1.jpg',
							'http://ots4cfy06.bkt.clouddn.com/1/l2.jpg',
							'http://ots4cfy06.bkt.clouddn.com/1/l3.jpg'
						],
						surface: [
							'http://ots4cfy06.bkt.clouddn.com/1/l4.jpg'
						]
					},
					rImg: {
						bottom: [
							'http://ots4cfy06.bkt.clouddn.com/1/r1.jpg',
							'http://ots4cfy06.bkt.clouddn.com/1/r2.jpg',
							'http://ots4cfy06.bkt.clouddn.com/1/r3.jpg',
							'http://ots4cfy06.bkt.clouddn.com/1/r4.jpg'
						],
						surface: [
							'http://ots4cfy06.bkt.clouddn.com/1/r5.jpg',
							'http://ots4cfy06.bkt.clouddn.com/1/r6.jpg'
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
							'http://ots4cfy06.bkt.clouddn.com/2/l1.jpg',
							'http://ots4cfy06.bkt.clouddn.com/2/l2.jpg'
						]

					},
					rImg: {
						bottom: [
							'http://ots4cfy06.bkt.clouddn.com/2/r1.jpg',
							'http://ots4cfy06.bkt.clouddn.com/2/r2.jpg'
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
							'http://ots4cfy06.bkt.clouddn.com/3/l1.jpg'
						],
						surface: [
							'http://ots4cfy06.bkt.clouddn.com/3/l2.jpg'
						]
					},
					rImg: {
						surface: [
							'http://ots4cfy06.bkt.clouddn.com/3/r1.jpg'
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
							'http://ots4cfy06.bkt.clouddn.com/4/l1.png',
							'http://ots4cfy06.bkt.clouddn.com/4/l2.jpg',
							'http://ots4cfy06.bkt.clouddn.com/4/l3.jpg'
						]
					},
					rImg: {
						bottom: [
							'http://ots4cfy06.bkt.clouddn.com/4/r1.jpg',
							'http://ots4cfy06.bkt.clouddn.com/4/r2.png',
							'http://ots4cfy06.bkt.clouddn.com/4/r4.jpg'
						],
						surface: [
							'http://ots4cfy06.bkt.clouddn.com/4/r3.png',
							'http://ots4cfy06.bkt.clouddn.com/4/r5.png'
						]
					}
			}
			],
			top: 0,
			bgTop: 0,
			bgUrl: 'http://ots4cfy06.bkt.clouddn.com/BG.png',
            imgSrc: "",
            clientX: 0,
            clientY: 0
		}
	},
	methods: {
		slider() {
			let cHeight = document.documentElement.clientHeight;
			let height = document.documentElement.scrollHeight;
			let scroll = document.documentElement.scrollTop;
			// console.log(scroll + cHeight !== height)
			if(scroll + cHeight !== height){
				this.top = -scroll/80;
				this.bgTop = scroll;
			}
		},
        clickImg(e) {
            var modal = document.getElementById("myModal");
            modal.style.display = "block";
            this.imgSrc = e.currentTarget.src;
            document.body.style.overflow = 'hidden';
            console.log()
            console.log(this.clientX, this.clientY);
        },

        closeModal(e) {
            var modal = document.getElementById("myModal");
            modal.style.display = "none";
            document.body.style.overflow = '';
            this.clientX = 0;
            this.clientY = 0;
			this.imgSrc = '';
        },

        mouse(e) {
            if (this.clientX === 0 || this.clientY === 0) {
                this.clientX = e.clientX;
                this.clientY = e.clientY;
            }
            var X = e.clientX - this.clientX;
            var Y = e.clientY - this.clientY;

            this.clientX = e.clientX;
            this.clientY = e.clientY;

            document.getElementById("myModal").scrollTop += Y * 3;
            document.getElementById("myModal").scrollLeft += X * 3;
        }
	},
	mounted() {
	    window.addEventListener('scroll', this.slider)
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.footer {
    position: absolute;
    width: 40%;
    left: 50%;
    bottom: 0;
    transform: translateX(-50%);
}
.modal {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 10; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: hidden; /* Enable scroll if needed */
  background-color: rgb(0, 0, 0); /* Fallback color */
  background-color: rgba(0, 0, 0, 0.9); /* Black w/ opacity */
}

.modal-content {
    position: absolute;
    margin: auto;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    animation-name: zoom;
    animation-duration: 1s;
}

@keyframes zoom {
  from {
    transform: scale(0);
  }
  to {
    transform: scale(1);
  }
}

.hello {
  height: 100%;
  overflow: hidden;
}
.surface {
	position: absolute;
	z-index: 2;
    pointer-events: none;
    transition: all .6s ease;
}
.surface div img  {
    pointer-events: all;
}
.bottom {
    transition: all .5s ease;
}
.right {
	display: inline-block;
	width: 30%;
}

.left {
	vertical-align: top;
	display: inline-block;
	width: 30%;
}
.left img {
	width: 100%;
    float: right;
}
.right img {
	width: 100%;
    float: left;
}
img {
    cursor: pointer;
}
@font-face {
	font-family: fzxk;
	src: url('http://ots4cfy06.bkt.clouddn.com/0/%E6%96%B9%E6%AD%A3%E8%A1%8C%E6%A5%B7_GBK.ttf')
}
.main {
	position: absolute;
    width: 35%;
    z-index: 3;
    left: 0;
    top: 0;
    right: 0;
    bottom: 85%;
    margin: auto;
}
.text {
	position: absolute;
	z-index: 3;
    text-align: left;
    pointer-events: none;
    transition: all .5s ease;
}
.text p {
	font-size: 2rem;
	text-shadow: 3px 4px 2px black;
}
.box {
	position: relative;
	height: 100%;
	width: 100%;
	background-size: 100%;
	background-repeat: no-repeat;
	transition: all .6s ease;
}
/******************第一块*********************/
.a0 {
    padding: 5% 0 10% 0;
}
.a0 .bottom .left img:nth-child(1) {
    width: 90%;

}
.a0 .bottom .left img:nth-child(2) {
    width: 80%;
    margin-top: 3%;
}
.a0 .bottom .left img:nth-child(3) {
    width: 120%;
    margin-top: 3%;
}
.a0 .bottom .right img:nth-child(1) {
    width: 80%;
    margin-top: -5%;
}
.a0 .bottom .right img:nth-child(2) {
    width: 60%;
    margin-top: 1%;
}
.a0 .bottom .right img:nth-child(3) {
    width: 100%;
    margin-top: 1%;
}
.a0 .bottom .right img:nth-child(4) {
    width: 67%;
    margin-top: 1%;
}
.surface div img {
    box-shadow: 5px -1px 8px 3px #00000066;
}
.a0 .surface .left {
    width: 16%;
    margin: 28% 8% 0 0;
}
.a0 .surface .right img:nth-child(1) {
    width: 50%;
    margin: 38% 0 0 55%;
}
.a0 .surface .right img:nth-child(2) {
    width: 60%;
    margin: 10% 0 0 65%;
}

.a0 .text {
    left: 0%;
    right: 0;
    top: 50%;
    bottom: 0;
    margin: auto;
}
.a0 .text .y-1958 {
    margin: 0 0 0 62%;
}

.a0 .text .y-1958 {
    margin: 0 0 0 62%;
}
.a0 .text .y-1958 p:nth-child(3) {
    font-size: 3rem;
}
.a0 .text .y-1962 {
    margin: -3% 0 0 20%;
}
.a0 .text .y-1962 p:nth-child(2) {
    font-size: 3rem;
}
.a0 .text .y-1995 {
    text-align: center;
    margin: 10% 0 0 0;
}
.a0 .text .y-1995 p:nth-child(6) {
    font-size: 4rem;
}
/*//////////////////////////////////// */

/*********************第二块*******************/
.a1 .bottom .left img:nth-child(1) {
    width: 120%;

}
.a1 .bottom .left img:nth-child(2) {
    width: 140%;
    margin-top: 3%;
}
.a1 .bottom .right img:nth-child(1) {
    width: 100%;
    margin-top: -5%;
}
.a1 .bottom .right img:nth-child(2) {
    width: 120%;
    margin-top: 1%;
}
.a1 .text {
    left: 20%;
    right: 0;
    top: 40%;
    bottom: 0;
    margin: auto;
}
.a1 .text .y-2008a {

}

.a1 .text .y-2008b {
    margin: -28% 0 0 51%;
}
.a1 .text .y-2012 {
    margin: 12% 0 0 50%;
}
.a1 .text .y-2014 {
       
}
.a1 .text .y-2015a {
    margin: 0% 0 0 50%; 
}

/*////////////////////////////////////*/

/**********************第三块************************/

.a2 {
    margin-top: 2%;
}
.a2 .bottom .left img {
    width: 200%;
    transform: translateX(50%);
}
.a2 .surface .left img {
    width: 115%;
    margin: 120% 0 0 0;
}
.a2 .surface .right img {
    width: 105%;
    margin: 100% 0 0 0;
}

.a2 .text {
    left: 15%;
    right: 0;
    top: 60%;
    bottom: 0;
    margin: auto;
}

.a2 .text .y-2017a {
    margin: 59% 0 0 7%;
}

/*///////////////////////////////////////////////////*/



/**********************第四块************************/

.a3 {
    margin-top: 28%;
}

.a3 .bottom .left img:nth-child(1) {
    width: 105%;
}
.a3 .bottom .left img:nth-child(2) {
    width: 80%;
    margin-top: 3%;
}
.a3 .bottom .left img:nth-child(3) {
    width: 110%;
    margin-top: 3%;
}
.a3 .bottom .right img:nth-child(1) {
    width: 105%;
    margin-top: -30%;
}
.a3 .bottom .right img:nth-child(2) {
    width: 105%;
    margin-top: 3%;
}
.a3 .bottom .right img:nth-child(3) {
    width: 110%;
    margin-top: 10%;
}
.a3 .surface .right img:nth-child(1) {
    width: 80%;
    margin: 22% 0 0 40%;
}
.a3 .surface .right img:nth-child(2) {
    width: 80%;
    margin: 104% 0 0 32%;
}
.a3 .text {
    left: 4%;
    right: 0;
    top: 90%;
    bottom: 0;
    margin: auto;
}
.a3 .text .y-2017b {
    margin-left: 20%;
}
.a3 .text .y-2018a {
    margin: 6% 0 0 50%;
}
.a3 .text .y-2018b {
    margin: 3% 0 0 20%;
}
/*///////////////////////////////////////////////////*/



p {
	color: white;
	font-family: 'fzxk';
    margin: 0;
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
