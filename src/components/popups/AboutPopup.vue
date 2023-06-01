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
            <h2 class="color-black">About Me</h2>
            <h3>Name: <p class="text">Maria Silva</p></h3>
            <h3>Age: <p class="text">23</p></h3>
            <h3>Country: <p class="text">Portugal</p></h3>
            <h3>Role: <p class="text">Frontend Developer | Creative Web Developer</p></h3>

            <!-- .divider {
  height: 51px;
  width: 2px;
  background-color: #715e5e;
  margin: 5px 10px 0;
} -->

            <h3>Interests: <p class="text">Art, Japanese, Reading, Movies, Games, Travel</p></h3>
         </div>
         <div v-else-if="selected==2">
            <h2 class="color-black">Life Goals</h2>
            <p class="text">When I'm 80 years old, I want to look back and think "Wow, what a great, happy life I had."
For that to happen, I want to conquer every kind of dream I have. I will travel the world, meet all kinds of people, and get the future I want by working towards it. I won't forget to take breaks and enjoy the moment, and experience new things even if they seem scary.</p>
         </div>
         <div v-else-if="selected==3">
            <h2 class="color-black">Core Values</h2>
            <p class="text">I believe people are not defined only by who they are right now. They are defined by who they want to be, and by what they do to get there.
My pursuit of many interests, hobbies, and artistic tendencies, along with continuous attempts at self-improvement made me who I am.
I want to keep learning, challenge, and better myself, and do interesting things that make life worth living.</p>
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
            { id: 1, name: 'About Me' },
            { id: 2, name: 'Goals' },
            { id: 3, name: 'Values' },
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