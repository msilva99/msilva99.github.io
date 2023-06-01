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
            <h2 class="color-black">Welcome!</h2>
            <p>Hello, this is a test!</p>
         </div>
         <div v-else-if="selected==2">
            <h2 class="color-black">Welcome again!</h2>
            <p>Can you read this?</p>
         </div>
         <div v-else-if="selected==3">
            <h2 class="color-black">Woooo!</h2>
            <p>Yay!! It works!!!</p>
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
            { id: 1, name: 'Welcome1' },
            { id: 2, name: 'Welcome2' },
            { id: 3, name: 'Welcome3' },
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