<template>
	<div id="app">
		<LoadingScreen  />
		<main>
			<div class="desktop parent">
				<div v-for="item in gridItems" :key="item.id" :class="`div${item.id}`" @click="openPopup(item.id-1)">
					<img class="imgSize" :src="item.img">
					<p class="imgSize">{{ item.name }}</p>
				</div>
			</div>
			<WelcomePopup class="popupSize" :style="{ zIndex: gridItems[0].zindex }" v-if="popupVisible[0]" @close-popup="closePopup(0)" />
			<CareerPopup class="popupSize" :style="{ zIndex: gridItems[1].zindex }" v-if="popupVisible[1]" @close-popup="closePopup(1)" />
			<ProjectsPopup class="popupSize" :style="{ zIndex: gridItems[2].zindex }" v-if="popupVisible[2]" @close-popup="closePopup(2)" />
			<ArtPopup class="popupSize" :style="{ zIndex: gridItems[3].zindex }" v-if="popupVisible[3]" @close-popup="closePopup(3)" />
			<AboutPopup class="popupSize" :style="{ zIndex: gridItems[5].zindex }" v-if="popupVisible[5]" @close-popup="closePopup(5)" />
			<!-- <HelloPopup class="popupSize" :style="{ zIndex: gridItems[6].zindex }" v-if="popupVisible[6]" @close-popup="closePopup(6)" />
			<ErrorPopup class="popupSize" :style="{ zIndex: gridItems[7].zindex }" v-if="popupVisible[7]" @close-popup="closePopup(7)" />
			<PopupsPopup class="popupSize" :style="{ zIndex: gridItems[8].zindex }" v-if="popupVisible[8]" @close-popup="closePopup(8)" /> -->
			<ContactPopup class="popupSize" :style="{ zIndex: gridItems[12].zindex }" v-if="popupVisible[12]" @close-popup="closePopup(12)" />
		</main>
	</div>
</template>

<script>
// import { RouterLink, RouterView } from 'vue-router'
import LoadingScreen from './components/LoadingScreen.vue';
import WelcomePopup from './components/popups/WelcomePopup.vue';
import CareerPopup from './components/popups/CareerPopup.vue';
import ProjectsPopup from './components/popups/ProjectsPopup.vue';
import ArtPopup from './components/popups/ArtPopup.vue';
import AboutPopup from './components/popups/AboutPopup.vue';
import ContactPopup from './components/popups/ContactPopup.vue';
// import HelloPopup from './components/popups/HelloPopup.vue';
// import ErrorPopup from './components/popups/ErrorPopup.vue';
// import PopupsPopup from './components/popups/PopupsPopup.vue';

export default {
	name: "App",
	components: {
		LoadingScreen,
		WelcomePopup,
		CareerPopup,
		ProjectsPopup,
		ArtPopup,
		AboutPopup,
		ContactPopup
		// HelloPopup,
		// ErrorPopup,
		// PopupsPopup,
	},
	data() {
	  	return {
			isLoading: true,
			gridItems: [
            { id: 1, zindex: 1, img: './src/assets/img/icon-welcome.png', name: 'Welcome' },
            { id: 2, zindex: 1, img: './src/assets/img/icon-career.png', name: 'Career' },
            { id: 3, zindex: 1, img: './src/assets/img/icon-projects.png', name: 'Projects' },
            { id: 4, zindex: 1, img: './src/assets/img/icon-art.png', name: 'Art' },
            // { id: 5, zindex: 1, img: 'https://cdn.discordapp.com/attachments/955611338850316399/1111286623217405984/image.png', name: '?' },
            { id: 6, zindex: 1, img: './src/assets/img/icon-about.png', name: 'About Me' },
            // { id: 7, zindex: 1, img: 'https://cdn.discordapp.com/attachments/955611338850316399/1111286623217405984/image.png', name: 'Hello' },
            // { id: 8, zindex: 1, img: 'https://cdn.discordapp.com/attachments/955611338850316399/1111286623217405984/image.png', name: 'Popups' },
            // { id: 9, zindex: 1, img: 'https://cdn.discordapp.com/attachments/955611338850316399/1111286623217405984/image.png', name: 'Error' },
            // { id: 10, zindex: 1, img: 'https://cdn.discordapp.com/attachments/955611338850316399/1111286623217405984/image.png', name: '?' },
            // { id: 11, zindex: 1, img: 'https://cdn.discordapp.com/attachments/955611338850316399/1111286623217405984/image.png', name: '?' },
            // { id: 12, zindex: 1, img: 'https://cdn.discordapp.com/attachments/955611338850316399/1111286623217405984/image.png', name: '?' },
            { id: 13, zindex: 1, img: './src/assets/img/icon-contact.png', name: 'Contact' },
            { id: 14, zindex: 1, img: './src/assets/img/icon-kohi.png', name: 'Ko-hi' }
         ],
			popupVisible: [false, false, false, false, false, false, false, false, false, false, false, false, false, false],
			maxZindex: 1
		};
	},
	methods: {
		openPopup(item) {
			this.maxZindex++;
			this.gridItems[item].zindex = this.maxZindex;
			this.popupVisible[item] = true;
		},
		closePopup(item) {
			this.popupVisible[item] = false;
		},
   },
	// watch: {
	// 	maxZindex(val) {
	// 		if (val > 998) {
				
	// 		} 
	// 	}
	// }
};
</script>


<style>

/* Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@300;400;500&family=Roboto+Slab:wght@300;400;500&family=Space+Grotesk:wght@300;400;500&family=Zilla+Slab:wght@300;400;500&display=swap');

@font-face {
   font-family: "Nokia";
   src: url("./assets/fonts/nokiafc22.eot");
   src: url("./assets/fonts/nokiafc22.eot") format("embedded-opentype"), url("./assets/fonts/nokiafc22.woff") format("woff"), url("./assets/fonts/nokiafc22.ttf") format("truetype");
   font-weight: normal;
   font-style: normal;
}

body {
	position: relative;
}
.desktop {
	width: 100vw;
	height: 100vh;
	position: absolute;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
   z-index: 1;
	/* display: flex;
	flex-direction: column;
  	flex-wrap: wrap; */
}
@media only screen and (min-width: 768px) {

	.popupSize {
		height: 65%;
		width: 60%;
		max-width: 800px;
		min-width: 700px;
		min-height: 450px;
	}
	.parent {
		display: grid;
		grid-template-columns: repeat(2, 1fr) 3fr repeat(2, 1fr);
		grid-template-rows: repeat(4, 1fr);
		grid-column-gap: 0px;
		grid-row-gap: 0px;
	}

	.imgSize {
		cursor: pointer;
	}
	img.imgSize {
		width: 70px;
		height: 70px;
	}
	p.imgSize {
		margin: 0;
		margin-top: 10px;
		font-family: 'Roboto Slab', serif;
		font-family: 'Space Grotesk', sans-serif;
		font-family: 'Roboto Mono', monospace;
		font-family: 'Zilla Slab', serif;
		font-weight: 600;
		font-weight: 400;
		font-weight: 500;
		font-size: 20px;
		font-size: 18px;
		font-size: 16px;
	}
	.parent div {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		text-align: center;
	}
	.div1 { grid-area: 1 / 1 / 2 / 2; }
	.div2 { grid-area: 1 / 2 / 2 / 3; }
	.div3 { grid-area: 2 / 1 / 3 / 2; }
	.div4 { grid-area: 2 / 2 / 3 / 3; }
	.div5 { grid-area: 3 / 2 / 4 / 3; }
	.div6 { grid-area: 3 / 1 / 4 / 2; }
	.div7 { grid-area: 1 / 4 / 2 / 5; }
	.div13 { grid-area: 1 / 5 / 2 / 6; }
	.div9 { grid-area: 2 / 4 / 3 / 5; }
	.div14 { grid-area: 2 / 5 / 3 / 6; }
	.div11 { grid-area: 3 / 4 / 4 / 5; }
	.div12 { grid-area: 3 / 5 / 4 / 6; }
	/* .div13 { grid-area: 4 / 4 / 5 / 5; }
	.div14 { grid-area: 4 / 5 / 5 / 6; } */

	/* Original Grid */
	/* .div1 { grid-area: 1 / 1 / 2 / 2; }
	.div2 { grid-area: 1 / 2 / 2 / 3; }
	.div3 { grid-area: 2 / 1 / 3 / 2; }
	.div4 { grid-area: 2 / 2 / 3 / 3; }
	.div5 { grid-area: 3 / 1 / 4 / 2; }
	.div6 { grid-area: 3 / 2 / 4 / 3; }
	.div7 { grid-area: 1 / 4 / 2 / 5; }
	.div8 { grid-area: 1 / 5 / 2 / 6; }
	.div9 { grid-area: 2 / 4 / 3 / 5; }
	.div10 { grid-area: 2 / 5 / 3 / 6; }
	.div11 { grid-area: 3 / 4 / 4 / 5; }
	.div12 { grid-area: 3 / 5 / 4 / 6; }
	.div13 { grid-area: 4 / 4 / 5 / 5; }
	.div14 { grid-area: 4 / 5 / 5 / 6; } */
}

header {
	line-height: 1.5;
	max-height: 100vh;
}

.logo {
	display: block;
	margin: 0 auto 2rem;
}

nav {
	width: 100%;
	font-size: 12px;
	text-align: center;
	margin-top: 2rem;
}

nav a.router-link-exact-active {
	color: var(--color-text);
}

nav a.router-link-exact-active:hover {
	background-color: transparent;
}

nav a {
	display: inline-block;
	padding: 0 1rem;
	border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
	border: 0;
}

@media (min-width: 1024px) {
	header {
		display: flex;
		place-items: center;
		padding-right: calc(var(--section-gap) / 2);
	}

	.logo {
		margin: 0 2rem 0 0;
	}

	header .wrapper {
		display: flex;
		place-items: flex-start;
		flex-wrap: wrap;
	}

	nav {
		text-align: left;
		margin-left: -1rem;
		font-size: 1rem;

		padding: 1rem 0;
		margin-top: 1rem;
	}
}


/* ------------------- */

.popup p {
	color: black;
	margin-top: 10px;
	font-family: 'Zilla Slab', serif;
	font-weight: 600;
	font-weight: 400;
	font-weight: 500;
	font-size: 18px;
}

.popup h3 {
	font-size: 16px;
	margin: 14px 2px;
}

.popup p.text {
	color: #422e2e;
	display: inline;
}

.absolute {
	position: absolute;
   margin: auto;
   top: 0;
   right: 0;
   bottom: 0;
   left: 0;
}
.draggable {
   cursor: move;
}

.popup {
   width: 100%;
   height: 100%;
   background-color: seashell;
   outline: #FFECE0 solid 2px;
   border: #110000 solid 3px;
   border-radius: 1px;
   position: relative;
   font-family: "Nokia";
   z-index: 2;
	padding: 52px 25px 0;
	display: flex;
}

.side-button {
	padding: 15px;
	font-family: 'Nokia', serif;
	font-weight: 500;
	font-size: 16px;
	border: solid 3px;
	text-align: center;
}

.side-button:hover {
	cursor: pointer;
}

.side-button--purple, a.side-button--purple:hover {
	background-color: plum;
	border-color: darkviolet;
	color: darkviolet;
}

.side-button--pink, a.side-button--pink:hover {
	background-color: pink;
	border-color: hotpink;
	color: hotpink;
}

.popup p, .popup h1, .popup h2, .popup h3, .popup h4, .popup h5, .popup h6 {
   color: #20191b;
}

.popup-header {
   position: absolute;
   top: 0;
	left: 0;
	right: 0;
   height: 32px;
   width: 100%;
   border-bottom: #110000 solid 3px;
   display: flex;
   justify-content: space-between;
   background-color: #eeb9d7;

   /* light pink #ff93d0 */
   /* lilac #c89beb */
   /* light blue #92bbf1 */
}

.popup-header-tabs {
   height: 100%;
   width: 90%;
   position: relative;
   display: flex;
}
.popup-header-tab {
   position: absolute;
   top: 0;
   bottom: 0;
   border-right: #110000 solid 3px;
	padding-bottom: 1.5px;
	display: flex;
	justify-content: center;
	align-items: end;
}
.popup-header-tab.tab-1 {
   background-color: #ff93d0;
}
.popup-header-tab.tab-1:not(.popup-header-tab--selected) h4 {
   color: #e45ba9;
}
.popup-header-tab.tab-2 {
   background-color: #c89beb;
}
.popup-header-tab.tab-2:not(.popup-header-tab--selected) h4 {
	color: #a845cb;
}
.popup-header-tab.tab-3 {
   background-color: #92bbf1;
}
.popup-header-tab.tab-3:not(.popup-header-tab--selected) h4 {
   color: #578cd2;
}
.popup-header-tab.tab-4 {
   background-color: #a9d5df;
}
.popup-header-tab.tab-4:not(.popup-header-tab--selected) h4 {
   color: #48a2b7;
}

.popup-header-tab--selected h4 {
	text-decoration: dotted white 4px underline;
	margin-bottom: 2px;
	color: white;
}

.popup-close {
   font-family: "Nokia";
   color: #110000;
   cursor: pointer;
   padding-top: 4px;
   padding-right: 4px;
}



</style>
