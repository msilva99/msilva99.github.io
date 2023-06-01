<template>
   <div :class="{ loader: true, fadeout: !isLoading }" v-on:mousemove="mousePos" >
      <svg v-bind:style="{ fill:'hsl(' + xPos+', 80%, 80%)' }" class="colorImg" fill="%23555111" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 45.532 45.532" xml:space="preserve"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <path d="M22.766,0.001C10.194,0.001,0,10.193,0,22.766s10.193,22.765,22.766,22.765c12.574,0,22.766-10.192,22.766-22.765 S35.34,0.001,22.766,0.001z M22.766,6.808c4.16,0,7.531,3.372,7.531,7.53c0,4.159-3.371,7.53-7.531,7.53 c-4.158,0-7.529-3.371-7.529-7.53C15.237,10.18,18.608,6.808,22.766,6.808z M22.761,39.579c-4.149,0-7.949-1.511-10.88-4.012 c-0.714-0.609-1.126-1.502-1.126-2.439c0-4.217,3.413-7.592,7.631-7.592h8.762c4.219,0,7.619,3.375,7.619,7.592 c0,0.938-0.41,1.829-1.125,2.438C30.712,38.068,26.911,39.579,22.761,39.579z"></path> </g> </g></svg>
      
      <h2>Maria Silva</h2>
      
      <div class="shell">
         <div class="bar" :style="{ width: progress + '%', background:'hsl(' + xPos + ', 80%, 80%)'}"></div>
      </div>
      
      <h4>Loading...</h4>
   </div>
 </template>
 
 <script>
 export default {
   name: "LoadingScreen",
   data() {
      return {
         progress: 0,
         xPos: 0,
         yPos: 0,
         isLoading: true,
         loadingBar: null
      }
   },
   beforeMount(){
      this.loadingBar = setInterval(this.makeProgress, 500);
   },
   methods: {
      makeProgress() {
         if (this.progress < 100) {
            this.progress += 20;
         } else {
            this.isLoading = false;
            clearInterval(this.loadingBar);
         }
      },
      mousePos(event) {
        this.xPos = event.offsetX;
        this.yPos = event.offsetY;
      },
   }
 };
 </script>
 
 <style>

.fadeout {
   animation: fadeout 1s forwards;
}

@keyframes fadeout {
   to {
      opacity: 0;
      visibility: hidden;
   }
}

.loader h1,.loader h2,.loader h3,.loader h4,.loader h5,.loader h6,.loader p {
   color: white;
}

/* Loading Bar */
.shell {
   height: 20px;
   width: 280px;
   outline: 2px solid white;
   border-radius: 9px;
   padding: 1.5px;
   margin: 40px 0 15px 0;
}
.bar {
  background: linear-gradient(to right, #B993D6, #8CA6DB);
  height: 100%;
  width: 15px;
  border-radius: 9px;
}

/* --- */

.loader {
   background-color: #261b32;
   color: white;
   font-size: 32px;
   overflow: hidden;
   position: fixed;
   bottom: 0;
   left: 0;
   right: 0;
   top: 0;
   display: flex;
   flex-direction: column;
   justify-content: center;
   align-items: center;
   text-align: center;
   z-index: 3;
}
.loader h2  {
   margin-bottom: 10vh;
}
.loader h4  {
   font-size: 26px;
}

svg.colorImg {
   fill:white;
   height: 150px;
   width: 150px;
}

</style>
