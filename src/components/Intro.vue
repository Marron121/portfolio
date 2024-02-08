<template>
    <h1>Hi! I'm Aaron:</h1>
    <h2>{{ currentTitleString }}</h2>
    <h3>passionate about UI/UX</h3>
    <Selector :buttons="buttonsData"></Selector>
</template>
<script>
//Components
import Selector from '@/components/SectionSelector.vue';
import Footer from '@/components/Footer.vue';
//Images
import workIcon from '@/assets/icons/works.svg';
import projectsIcon from '@/assets/icons/projects.svg';
import contactIcon from '@/assets/icons/about.svg';
//Components - Pages
import Work from '@/components/Work.vue';
import Projects from '@/components/Projects.vue';
import About from '@/components/About.vue';
export default {
    components: {Selector, Footer},
    data(){
        return{
            currentTitleInt : 0,
            currentTitleString: "",
            currentTitleChar: 0,
            titles: ['Programmer', 'Game Developer', 'Web Developer'],
            times: [75, 1000],
            currentIntervalID : 0,
            buttonsData: [
                { name: 'Work', icon: workIcon, component: Work },
                { name: 'Projects', icon: projectsIcon, component: Projects },
                { name: 'About', icon: contactIcon, component: About }
            ]
        };
    },
    methods: {
        AddTextValue(){
            let writingString = this.titles[this.currentTitleInt];
            this.currentTitleString = writingString.substring(0,this.currentTitleChar)
            this.currentTitleString+= '_';
            this.currentTitleChar+=1;
            if ( this.currentTitleChar > writingString.length){
                clearInterval(this.currentIntervalID);
                this.currentIntervalID = setTimeout(this.WaitTextValue, this.times[1]);
                this.currentTitleChar = 0;
            }
        },
        WaitTextValue(){
            clearInterval(this.currentIntervalID);
            this.currentIntervalID = setInterval(this.DeleteTextValue, this.times[0]);
        },
        DeleteTextValue(){
            this.currentTitleString = this.currentTitleString.slice(0,this.currentTitleString.length-2);
            this.currentTitleString+= '_';
            if (this.currentTitleString == "_"){
                this.currentTitleInt +=1;
                if (this.currentTitleInt > this.titles.length-1){
                    this.currentTitleInt = 0;
                }
                clearInterval(this.currentIntervalID);
                this.currentIntervalID = setInterval(this.AddTextValue, this.times[0]);
            }
        }
    },
    created(){
        //console.log("Tamos aqui en inicio.");
        this.currentIntervalID = setInterval(this.AddTextValue, this.times[0]);
    }
}
</script>
<style scoped>
h1,h2,h3{
    justify-self: center;
    align-self: center;
    align-content: center;
    align-items: center;
}
</style>