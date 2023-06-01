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
            <h2 class="color-black">Work Experience</h2>
            <h3>Junior Consultant<br>Frontend Developer</h3>
            <p class="text">June 2022 - Now<br>VILT, Braga</p>
            <br>
            <h3>Professional Services Trainee</h3>
            <p class="text">Sept 2021 - June 2022<br>VILT, Braga</p>
         </div>
         <div v-else-if="selected==2">
            <h2 class="color-black">Skills & Interests</h2>
            <h3>Vue.js, Vuetify</h3>
            <h3>HTML, CSS, JS</h3>
            <h3>Adobe XD, Figma</h3>
            <h3>jQuery</h3>
            <h3>Bootstrap</h3>
            <h3>SASS/SCSS</h3>
            <p>See more here: <button>My CV</button></p>
         </div>
         <div v-else-if="selected==3">
            <h2 class="color-black">Education</h2>
            <h3>[BSc] Bachelor in Software Engineering</h3>
            <p class="text">2017 - 2020<br>University of Minho</p>
            <br>
            <h3>[MSc] Masters in Software Engineering</h3>
            <p>2020 - 2022<br>University of Minho</p>
         </div>
         <div v-else-if="selected==4">
            <h2 class="color-black">Training</h2>
            <h3>Web Development [From 0 to advanced]</h3>
            <h4>Udemy</h4>
            <p class="text">Udemy course that teaches concepts about how to create a website using HTML, CSS and SASS</p>
            <br>
            <h3>English Excellence Program</h3>
            <h4>Speexx</h4>
            <p class="text">Excellence level description - "((note on hover))"</p>
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
            { id: 1, name: 'Work' },
            { id: 2, name: 'Skills' },
            { id: 3, name: 'Education' },
            { id: 4, name: 'Training' },
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
   }
}
</script>