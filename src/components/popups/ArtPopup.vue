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
            <h2 class="color-black"> My Art</h2>
            <a href=""><h3>Commissions website link here</h3></a>
            <p class="text">*Commissions are closed at this moment.*</p>
            <br>
            <h3>Check out my socials:</h3>
            <p>*Tiktok*  *Insta*</p>
         </div>
         <div v-if="selected==2">
            <h2 class="color-black"> Why Art</h2>
            <p class="text">Art has been a part of me ever since I was little. As a kid, I used to watch 'Art Attack' and tried to do my own little art projects. Growing up, I continued drawing, and trying to improve. I used to want to make it my full-time job, but I learned that when you make such a hobby your obligation, you soon start to feel less relaxed when doing it. To me, creating art is a way to express myself and relax, and I want to keep it that way.</p>
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
            { id: 1, name: 'My Art' },
            { id: 2, name: 'Why Art' },
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