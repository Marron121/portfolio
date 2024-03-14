<template>
    <div class="imageDisplay">
        <img class="image" v-bind:src="images[currentImage]"/>
        <div class="slideshowControls" v-if="images.length > 1">
            <div class="prevButton" v-on:click="changeImageManual(-1)">{{"<"}}</div>
            <div class="automaticButton" v-on:click="slideshowStatusChanged()">{{states[currentState] + " slideshow"}}</div>
            <div class="nextButton" v-on:click="changeImageManual(1)">{{">"}}</div>
        </div>
    </div>
</template>
<script>
export default{
    props:{
        images: {
            type: Array,
            required: true,
            default: () => []
        }
    },
    data(){
        return{
            currentImage: 0,
            timer: null,
            currentState: 1,
            states: ["Start", "Stop"]
        }
    },
    mounted(){
        this.startSlideShow();
    },
    beforeUnmount(){
        this.stopSlideshow();
    },
    methods:{
        startSlideShow(){
            if (this.images.length >= 2){
                this.timer = setInterval(this.updateImage,1500);
            }
        },
        stopSlideshow(){
            clearInterval(this.timer);
        },
        updateImage(value = 1){
            this.currentImage+=value;
            if (this.currentImage>=this.images.length){
                this.currentImage = 0;
            }
            else if (this.currentImage <= -1){
                this.currentImage = this.images.length-1;
            }
        },
        slideshowStatusChanged(){
            if(this.currentState == 0){
                this.currentState = 1;
                this.startSlideShow();
            }
            else{
                this.currentState = 0;
                this.stopSlideshow();
            }
        },
        changeImageManual(value){
            this.updateImage(value);
            if (this.currentState == 1){
                this.slideshowStatusChanged();
            }
        }
    }

}
</script>
<style scoped>
.imageDisplay{
    display: block;
    justify-content: center;
    min-width: 50%;
    width: 50%;
    margin-top: 1%;
    margin-bottom: 1%;
}
.image{
    height: auto;
    max-height: 520px;
    width: 100%;
    object-fit: scale-down;
}
.slideshowControls{
    display: flex;
    position:relative;
    bottom: 10%;
    width: 100%;
    justify-content: center;
    align-items: center;
    gap: 10px;
}
.automaticButton{
    padding-left: 25px;
    padding-right: 25px;
    width: fit-content;
    height: fit-content;
    border-radius: 5px;
    color: var(--color-black);
    font-weight: bold;
    background-color: var(--color-blue-dark-4);
    cursor: pointer;
    transition: 0.5s;
}
.prevButton, .nextButton{
    width: fit-content;
    height: fit-content;
    padding: 5px;
    border-radius: 5px;
    color: var(--color-slideshow-text);
    font-weight: bold;
    background-color: var(--color-slideshow);
    cursor: pointer;
    transition: 0.5s;
}
.automaticButton:hover, .nextButton:hover, .prevButton:hover{
    background-color: var(--color-slideshow-hover);
    box-shadow: 0 0 20px 0px var(--color-slideshow-hover);
}
</style>