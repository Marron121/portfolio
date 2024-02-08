<template>
    <h2>Projects</h2>
    <p>Which kind of projects do you want to know more about?</p>
    <Selector :buttons="buttonsData"></Selector>
</template>
<script>
import Selector from '@/components/SectionSelector.vue';
//Images
import gamesIcon from '@/assets/icons/videogames.svg';
import generalIcon from '@/assets/icons/developments.svg';
import videosIcon from '@/assets/icons/videos.svg';
//Components - Pages
import Videogames from '@/components/ProjectsGames.vue';
import General from '@/components/ProjectsProgrammer.vue';
import Videos from '@/components/ProjectsOther.vue';
export default{
    components: { Selector },
    data(){
        return{
            activeSection: '',
            buttonsData:[
                { name: 'Videogames', icon: gamesIcon, component: Videogames },
                { name: 'App & Web development', icon: generalIcon, component: General },
                { name: 'Video Editing', icon: videosIcon, component: Videos }
            ]
        }
        
    }
}
</script>