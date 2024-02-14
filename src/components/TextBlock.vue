<template>
    <div class="textBlock-area">
        <h3>{{ title }}</h3>
        <div class="textBlock-visuals">
            <ImageDisplay v-if="imagesData.length>0"
            :images="imagesData">
            </ImageDisplay>
            <div v-if="videoData != ''">
                <video controls>
                <source v-bind:src="videoData" type="video/mp4">
                </video>
            </div>
        </div>
        <div class="textBlock-description" v-html="currentDescription"></div>
        <div v-if="tasks!=''">
            <div v-bind:class="taskButtonClass" @click="ChangeHighlithsVisibility">Highlights</div>
            <Transition name="fade">
                <div v-if="taskClass=='tasksActive-list'" v-bind:class="taskClass"><p v-html="tasks"></p></div>
            </Transition>
        </div>
        <div class="textBlock-button" v-if="buttonData.length>0">
            <ButtonWithIcon
            :text="buttonData[0].name"
            :icon="buttonData[0].icon"
            :url="buttonData[0].url">
            </ButtonWithIcon>
        </div>
    </div>
</template>
<script>
import ButtonWithIcon from '@/components/ButtonWithIcon.vue';
import ImageDisplay from '@/components/ImageDisplay.vue';
export default{
    components: { ButtonWithIcon, ImageDisplay},
    props: {
        title: {
            type: String,
            required : true
        },
        description: {
            type: String,
            required : true
        },
        tasks: {
            type: String,
            required: false,
            default: ''
        },
        imagesData: {
            type: Array,
            required: true,
            default: () => []
        },
        videoData:{
            type: String,
            required: false,
            default: ''
        },
        buttonData: {
            type: Array,
            required: false,
            default: ()=> []
        }
    },
    data(){
        return{
            intervalID:0,
            timeForLetter:50,
            currentDescription:"",
            currentLetter:0,
            taskClass: 'tasksInactive-list',
            taskButtonClass: 'tasksInactive-button'
        }
    },
    methods: {
        ChangeHighlithsVisibility(){
            if (this.taskClass == 'tasksInactive-list'){
                this.taskClass = 'tasksActive-list';
                this.taskButtonClass = 'tasksActive-button';
                scrollTo()
            }
            else{
                this.taskClass = 'tasksInactive-list';
                this.taskButtonClass = 'tasksInactive-button';
            }
        }

    },
    mounted(){
        this.currentDescription= this.description;
    }
}
</script>
<style scoped>
h3{
    font-weight: bold;
}
.textBlock-description{
    text-align: center;
    color: #CAF0F8;
}
.textBlock-area{
    width: 100%;
    display: block;
    padding: 1%;
    margin-top: 1%;
    border-style: solid;
    border-color: #023E8A;
    transition: all 0.5s;
}
.textBlock-area:hover{
    border-radius: 2%;
    box-shadow: 0 0 10px 5px #023E8A;
}
.textBlock-visuals{
    display: inline-flex;
    gap: 10px;
    justify-content: center;
    align-content: center;
    align-items: center;
    justify-self: center;
    width: 100%;
    max-width: 100%;
    max-height: 720px;
    padding: 1%;
    margin-bottom: 1%;
    border-style: solid;
    border-width: 0px 0px 10px 0px;
    border-radius: 20px;
    border-color: #023E8A;
}
.imageDisplay{
    width: 45% !important;
}
video {
    width: 100%;
    height: auto;
    object-fit: scale-down;
}
.textBlock-button{
    width: fit-content;
    height: fit-content;
    margin: auto;
    margin-top: 1%;
    margin-bottom: 1%;
}
.tasksActive-button, .tasksInactive-button {
    min-height: fit-content;
    min-width: fit-content;
    height: fit-content;
    margin: auto;
    margin-top: 1%;
    margin-bottom: 1%;
    padding: 2%;
    border-radius: 5px;
    color: black;
    text-align: center;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.5s;
}
.tasksInactive-button{
    width: fit-content;
    background-color: #0096C7;
    border-color: #0096C7;
    transition: all 0.5s;
}
.tasksActive-button{
    width: 70%;
    background-color: #023E8A;
    border-color: #023E8A;
    transition: all 0.5s;
}
.tasksActive-list{
    min-height: fit-content;
    min-width: fit-content;
    width: 70%;
    margin: auto;
    margin-top: 1%;
    margin-bottom: 1%;
    padding-top: 2%;
    padding-bottom: 2%;
    border-radius: 5px;
    background-color: #023E8A;
    border-color: #023E8A;
    transition: 0.5s;
}
.tasksInactive-button:hover{
    background-color: #0077B6;
    border-color: #0077B6;
    box-shadow: 0 0 20px 0px #0077B6;
}
.tasksActive-button:hover{
    background-color: #023E8A;
    border-color: #023E8A;
    box-shadow: 0 0 20px 0px #023E8A;
}

.fade-enter-active, .fade-leave-active{
  transition: all 0.5s ease;
}

.fade-enter-from{
    opacity: 0;
    transform: translateY(1vh);
}
.fade-leave-to {
    opacity: 0;
    transform: translateY(-1vh);
}
</style>