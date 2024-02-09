<template>
    <div v-for="work in works" :key="work.id">
        <TextBlock
            :title="work.title"
            :description="work.description"
            :tasks="work.tasks"
            :imagesData="work.images"
            :buttonData="work.buttonData"
        ></TextBlock>
    </div>
</template>
<script>
//Components
import TextBlock from '@/components/TextBlock.vue';
//Icons
import GithubIcon from '@/assets/icons/github.svg';
import WebpageIcon from '@/assets/icons/webpage.svg';
//Images
import dm_1 from '@/assets/screenshots/dm/dm_1.gif';
import a3_1 from '@/assets/screenshots/a3/a3_1.png';
import a3_2 from '@/assets/screenshots/a3/a3_2.png';
import a3_3 from '@/assets/screenshots/a3/a3_3.png';
import p_1 from '@/assets/screenshots/portfolio/p1.png';
export default{
    components: {
        TextBlock,
    },
    data(){
        return{
            works:[
            {
                id: 1,
                title: "Dialogue Maker",
                description: "Open-source tool that automatically formats dialogue lines to a JSON format.",
                tasks: "<ul><li>Simple interface.</li><li>Load/Save functionality.</li><li>Options to modify the look of the application.</li></ul>",
                images: [dm_1],
                buttonData: [{name: 'Check the source code', icon: GithubIcon, url: 'https://github.com/Marron121/DialogueMaker'}]
            },
            {
                id: 2,
                title: "A3 webpage",
                description: "Webpage for the second edition of the <i>Aaron's Awesome Games Festival</i>, an event where people show trailers for their games.<br/>I helped to create the page, including the display of images on the site.",
                images: [a3_1, a3_2, a3_3],
                buttonData: [{name: 'Check the webpage', icon: WebpageIcon, url: 'https://lluispalerm.github.io/aaronawesomefestival/'}]
            },
            {
                id: 3,
                title: "Portfolio",
                description: "This entire portfolio you're currently viewing was created completely by me using <i>Vue 3</i>.",
                images: [p_1],
                buttonData: [{name: 'Check the source code', icon: GithubIcon, url: 'https://github.com/Marron121/portfolio'}]
            }
            ]
        }
    }
}
</script>