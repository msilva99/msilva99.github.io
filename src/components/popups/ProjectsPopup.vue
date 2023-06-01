<template>
   <div class="absolute">
      <div class="popup">
         <div class="popup-header draggable">
            <div class="popup-header-tabs">
            <div v-for="tab in tabs" :key="tab.id" :style=" { left: `calc(${tab.id-1}*100%/${tabs.length})`, width: `calc(100%/${tabs.length})`}" :class="[{ 'popup-header-tab--selected': selected==tab.id }, 'popup-header-tab', `tab-${tab.id}`]" @click="selectTab(tab.id)">
               <h4>{{ tab.name }}</h4>
				</div>
            </div>
            <h4 class="popup-close" @click="closePopup">X</h4>
         </div>
         <div v-if="selected==1">
            <h2 class="color-black">Projects</h2>
            <a href=""><h3>Japanese Flashcards</h3></a>
            <p class="text">During the pandemic, I started learning Japanese, and I made some spreadsheets with japanese words, along with their readings and meanings. I wanted to put those in flashcards, but regular flashcard apps only allow you to have two sides. I wanted more, as sometimes I wanted to show only the pronounciation, or only the meaning, so I created a quick solution. This was a fun experiment with Vue.js made in 2 days.</p>
         </div>
         <div v-if="selected==1" style="display: flex;flex-direction: column;justify-content: space-evenly;margin: 0 10px 0 35px; min-width: 170px;">
            <a class="side-button side-button--pink" href="https://msilva99.github.io/Japanese-Core/" target="_blank">Website</a>
            <button class="side-button side-button--pink">Open Gallery</button>
            <!-- <a class="side-button side-button--pink" href="https://github.com/msilva99/Japanese-Core" target="_blank">Github</a> -->
         </div>
         <div v-if="selected==2">
            <h2 class="color-black">Projects</h2>
            <a href=""><h3>Read2Be</h3></a>
            <p class="text">Feb 2021 - Jun 2021</p>
            <p class="text">Our final BSc project was LEI (Software Engineering Project). For this, me and my friends wanted to make a webapp that allowed us to save our 'plan-to-read' books, as well as the 'reading', 'dropped', and 'finished' ones. I was responsible for the frontend of this, using Vue.js and Vuetify. At the time, it was challenging, as I had to learn HTML, CSS, JS and Vue.js in less than a semester, but it was an amazing learning experience.</p>
         </div>
         <div v-if="selected==2" style="display: flex;flex-direction: column;justify-content: space-evenly;margin: 0 10px 0 35px; min-width: 170px;">
            <button class="side-button side-button--purple">Open Gallery</button>
            <a class="side-button side-button--purple" href="" target="_blank">Frontend Report (EN)</a>
            <a class="side-button side-button--purple" href="https://github.com/K1llByte/read2be/blob/master/report.pdf" target="_blank">Full Report (PT)</a>
            <a class="side-button side-button--purple" href="https://github.com/K1llByte/read2be" target="_blank">Github</a>
         </div>
      </div>
   </div>
</template>

<script>

export default {
   data() {
	  	return {
         selected: 1,
         tabs: [
            { id: 1, name: 'Japanese Flashcards' },
            { id: 2, name: 'Read2Be' },
         ],
      }
   },
   methods: {
      closePopup() {
         this.$emit('close-popup');
      },
      selectTab(id) {
         this.selected = id;
      }
   },
}
</script>