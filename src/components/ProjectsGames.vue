<template>
        <div v-for="work in works" :key="work.id">
            <TextBlock
                :title="work.title"
                :description="work.description"
                :tasks="work.tasks"
                :imagesData="work.images"
                :videoData="work.video"
                :buttonData="work.buttonData"
            ></TextBlock>
        </div>
</template>
<script>
//Components
import TextBlock from '@/components/TextBlock.vue';
//Icons
import ItchioIcon from '@/assets/icons/itchio.svg';
//Images - ASTBTS
import astbts_1 from '@/assets/screenshots/astbts/astbts_1.jpg';
import astbts_2 from '@/assets/screenshots/astbts/astbts_2.jpg';
import astbts_3 from '@/assets/screenshots/astbts/astbts_3.jpg';
import astbts_showcase from '@/assets/videos/astbts_programming.mp4';
//Images - Estrellada
import estrellada_1 from '@/assets/screenshots/estrellada/estrellada_1.png';
import estrellada_2 from '@/assets/screenshots/estrellada/estrellada_2.png';
import estrellada_3 from '@/assets/screenshots/estrellada/estrellada_3.png';
//Images - Error 404
import e404_1 from '@/assets/screenshots/e404/e404_1.png';
import e404_2 from '@/assets/screenshots/e404/e404_2.png';
import e404_3 from '@/assets/screenshots/e404/e404_3.png';
export default{
    components: {
        TextBlock,
    },
    data(){
        return{
            works:[
            {
                id: 1,
                title: "A Story Told By The Stars",
                description: "One hour long narrative game where you make constellations to learn the story of the main characters, <span class=\"bold\">developed with Unity</span>.",
                tasks: "<ul><li><span class=\"bold\">Director</span>.</li><li><span class=\"bold\">Audio designer.</span></li><li>Main <span class=\"bold\">writer</span>.</li><li><span class=\"bold\">Programmer</span> of the entire project, with the following highlights:</li><ul><li>Constellation creation.</li><li>Dialogue system that allowed different speeds, languages and auto-adjustable text size.</li><li>Level select screen after game completion.</li></ul></ul>",
                images: [astbts_1, astbts_2, astbts_3],
                video: astbts_showcase,
                buttonData: [{name: 'Play it for free', icon: ItchioIcon, url: 'https://aurum-lingua-games.itch.io/a-story-told-by-the-stars'}]
            },
            {
                id: 2,
                title: "Error404: Ecosystem Not Found",
                description: "Small puzzle game for the <i>Level Up Game Jam 2023</i>, <span class=\"bold\">developed with Unity</span>.",
                tasks: "<ul><li>Multi language.</li><li>Seamless transitions between levels.</li></ul>",
                images: [e404_1, e404_2, e404_3],
                buttonData: [{name: 'Play it for free', icon: ItchioIcon, url: 'https://lauraqwerty.itch.io/error-404-ecosystem-not-found'}]
            },
            {
                id: 3,
                title: "Estrellada",
                description: "Small platformer for the <i>Indie Spain Jam 2023</i>, <span class=\"bold\">developed with Godot</span>. I worked as the main programmer.",
                images: [estrellada_1, estrellada_2, estrellada_3],
                buttonData: [{name: 'Play it for free', icon: ItchioIcon, url: 'https://marron121.itch.io/estrellada'}]
            }
            ]
        }
    }
}
</script>