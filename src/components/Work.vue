<template>
    <h2>Professional work</h2>
    <div v-for="work in works">
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
import TextBlock from '@/components/TextBlock.vue';
import PlayStoreIcon from '@/assets/icons/playstore.svg';
//Images - Outland Odyssey
import oo_1 from '@/assets/screenshots/oo/oo_1.png';
import oo_2 from '@/assets/screenshots/oo/oo_2.jpg';
import oo_3 from '@/assets/screenshots/oo/oo_3.jpg';
import oo_4 from '@/assets/screenshots/oo/oo_4.png';
import oo_5 from '@/assets/screenshots/oo/oo_5.jpg';
import oo_6 from '@/assets/screenshots/oo/oo_6.png';
import oo_7 from '@/assets/screenshots/oo/oo_7.png';
import oo_8 from '@/assets/screenshots/oo/oo_8.jpg';
import oo_9 from '@/assets/screenshots/oo/oo_9.jpg';
import oo_trailer from '@/assets/Videos/oo_verticaltrailer.mp4';
export default{
    components: { TextBlock },
    data(){
        return{
            works:[
            {
                id: 1,
                title: "Outland Odyssey",
                description: "Action RPG for mobile phones <span class=\"bold\">developed with Unity</span>. <br /><i><span class=\"bold\">Outland Odyssey</span> is property of <b>Project SEED</b>. The visual elements are just to give visual aid of my work.</i>",
                tasks: "<ul><li>Main programmer of the entire <span class=\"bold\">UI/UX</span>.</li><li>Programmer of the <span class=\"bold\">audio system</span> and functionality.</li><li>Generalist programmer, incluing <span class=\"bold\">bug fixing</span> on areas like combat and audio.</li><li><span class=\"bold\">Create documentation</span> for systems like UI, quest system and more.</li><li><span class=\"bold\">Version control</span> of the project, creating builds and managing the branch system with <span class=\"bold\">Git/Github</span>.</li><li>Constant performance improvement via <span class=\"bold\">code and asset optimization</span>.</li></ul>",
                images: [oo_1, oo_2, oo_3, oo_4, oo_5, oo_6, oo_7, oo_8, oo_9],
                video: oo_trailer,
                buttonData: [{name: 'Check the Play Store', icon: PlayStoreIcon, url: 'https://play.google.com/store/apps/details?id=com.PTBenihPermainanInternasional.OutlandOdyssey&hl=en_US'}]
            }
            ]
        }
    }
}
</script>