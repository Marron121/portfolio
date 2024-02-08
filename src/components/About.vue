<template>
    <h2>Hello!</h2>
    <p>My name is Aaron. I was born in 1998, and since I was little I've had a huge passion for videogames, which led me to graduate from a game development & design course.</p>
    <p>As I worked on more and more projects I realized that I especially loved the <span class="bold">design & programming of the UI/UX</span>, so I focused on it while trying new technologies and improving my work.</p>
    <div class="about-imageWithText">
        <img v-bind:src="pic" class="about-myImage" v-on:mouseenter="ChangeTextVisibility" v-on:mouseleave="ChangeTextVisibility"/>
        <div>
            <h2>Scroll over my picture to know more!</h2>
            <ul v-bind:class="styleText">
            <li>Graduated from the <span class="bold">Game Development & Design Course</span> at University of Girona (UdG)</li>
            <li>3 years of <span class="bold">professional gamedev experience</span>.</li>
            <li>Experience with <span class="bold">Unity</span>, <span class="bold">Godot</span>, <span class="bold">Unreal Engine</span>, and more.</li>
            <li>Experience with <span class="bold">C#</span>, <span class="bold">Python</span>, <span class="bold">Javascript</span>, and more.</li>
            <li><span class="bold">Developed +20 projects</span>, including games and open-source programs.</li>
        </ul>
        </div>
    </div>
    <div class="about-buttons">
        <ButtonWithIcon
        :text="buttonEmailData[0].name"
        :icon="buttonEmailData[0].icon"
        :url="buttonEmailData[0].url"
        ></ButtonWithIcon>
        <ButtonWithIcon
        :text="buttonGithubData[0].name"
        :icon="buttonGithubData[0].icon"
        :url="buttonGithubData[0].url"
        ></ButtonWithIcon>
        <ButtonWithIcon
        :text="buttonItchioData[0].name"
        :icon="buttonItchioData[0].icon"
        :url="buttonItchioData[0].url"
        ></ButtonWithIcon>
    </div>
    <div class="about-credits">
        <div v-bind:class="creditsButtonClass" @click="ChangeCreditsVisibility">Credits for the icons</div>
            <Transition name="fade">
                <div v-if="creditsClass=='about-creditsVisible'" v-bind:class="creditsClass">
                    <ul>
                        <li><a href="https://thenounproject.com/icon/person-6357431/" target="_blank"><span class="bold">Person</span> by Kiki Rizky (The Noun Project)</a></li>
                        <li><a href="https://thenounproject.com/icon/development-6356314/" target="_blank"><span class="bold">Development</span> by HAZHA (The Noun Project)</a></li>
                        <li><a href="https://thenounproject.com/icon/email-6529498/" target="_blank"><span class="bold">Email</span> by Rudi Yugana (The Noun Project)</a></li>
                        <li><a href="https://github.com/logos" target="_blank"><span class="bold">Github</span> by GitHub, Inc.</a></li>
                        <li><a href="https://itch.io/press-kit" target="_blank"><span class="bold">Itch.io</span> by itch corp</a></li>
                        <li><a href="https://icons8.com/icon/8808/linkedin" target="_blank"><span class="bold">LinkedIn</span> from Icons8</a></li>
                        <li><a href="https://joinmastodon.org/es/branding" target="_blank"><span class="bold">Mastodon</span> by Mastodon gGmbH.</a></li>
                        <li><a href="https://thenounproject.com/icon/playstore-3428241/" target="_blank"><span class="bold">Playstore</span> by SBTS (The Noun Project)</a></li>
                        <li><a href="https://thenounproject.com/icon/project-3361457/" target="_blank"><span class="bold">Projects</span> by Adriansyah (The Noun Project)</a></li>
                        <li><a href="https://thenounproject.com/icon/videogame-controller-4885037/" target="_blank"><span class="bold">Videogame controller</span> by Lucas Helle (The Noun Project)</a></li>
                        <li><a href="https://thenounproject.com/icon/video-editing-4724366/" target="_blank"><span class="bold">Video editing</span> by Candy Design (The Noun Project)</a></li>
                        <li><a href="https://thenounproject.com/icon/webpage-2031125/" target="_blank"><span class="bold">Webpage</span> by Mahesh Keshvala (The Noun Project)</a></li>
                        <li><a href="https://thenounproject.com/icon/work-6222783/" target="_blank"><span class="bold">Work</span> by kumakamu (The Noun Project)</a></li>
                    </ul>
                </div>
            </Transition>
    </div>
    
</template>
<script>
//Icons
import ButtonWithIcon from '@/components/ButtonWithIcon.vue';
import GithubIcon from '@/assets/icons/github.svg';
import EmailIcon from '@/assets/icons/email.svg';
import ItchioIcon from '@/assets/icons/itchio.svg';
import Picture from '@/assets/icons/pfp.png';
export default {
    components: {ButtonWithIcon},
    data(){
        return{
            buttonGithubData: [{name: 'Check my github', icon: GithubIcon, url: 'https://github.com/Marron121'}],
            buttonEmailData: [{name: 'Send me an email', icon: EmailIcon, url: 'mailto:aaronmigo2.0@gmail.com'}],
            buttonItchioData: [{name: 'Check my projects', icon: ItchioIcon, url: 'https://marron121.itch.io/'}],
            pic : Picture,
            styleText: "about-bulletPointsInvisible",
            creditsButtonClass: 'about-creditsButtonInvisible',
            creditsClass: 'about-creditsInvisible'
        }
    },
    methods: {
        ChangeTextVisibility(){
            if (this.styleText == 'about-bulletPointsInvisible')
            {
                this.styleText = 'about-bulletPointsVisible';
            }
            else
            {
                this.styleText = 'about-bulletPointsInvisible';
            }
        },
        ChangeCreditsVisibility(){
            if (this.creditsButtonClass == 'about-creditsButtonInvisible')
            {
                this.creditsButtonClass = 'about-creditsButtonVisible';
                this.creditsClass = 'about-creditsVisible'
            }
            else
            {
                this.creditsButtonClass = 'about-creditsButtonInvisible';
                this.creditsClass = 'about-creditsInvisible'
            }
        }
    }
}
</script>
<style>
.about-imageWithText{
    display: grid;
    max-height: 400px;
    grid-template-columns: 1fr 3fr;
    gap: 1%;
    justify-items: left;
    align-items:flex-start;
    margin-top: 1%;
    margin-bottom: 1%;
    border-style: solid;
    border-color: #023E8A;
    transition: all 0.5s;
}
.about-imageWithText:hover{
    box-shadow: 0 0 10px 5px #023E8A;
}
.about-bulletPointsInvisible{
    color: transparent;
    transition: 0.5s;
}
.about-bulletPointsVisible{
    color: #CAF0F8;
    transition: 0.5s;
}
.about-myImage{
    margin: auto;
    height: 300px;
    max-height: 300px;
    width: 100%;
    object-fit: contain;
    transition: 0.5s ease;
}
.about-myImage:hover{
    background-color: #023E8A;
}
.about-buttons{
    width: auto;
    justify-self: center;
    display: inline-flex;
    justify-content: center;
    gap: 5%;
    padding-top: 1%;
}
.about-imageCredits{
    margin-top: 1%;
    margin-bottom: 1%;
}
.about-creditsButtonVisible, .about-creditsButtonInvisible{
    padding: 0.5%;
    margin-top: 2%;
    width: fit-content;
    height: fit-content;
    transition: 0.5s ease-in;
    color: black;
    font-weight: bold;
}
.about-creditsButtonVisible{
    background-color: #023E8A;
}
.about-creditsButtonVisible:hover{
    box-shadow: 0 0 10px 0px #023E8A;
}
.about-creditsButtonInvisible{
    background-color: #0096C7;
}
.about-creditsButtonInvisible:hover{
    box-shadow: 0 0 10px 5px #0096C7;
}
.about-creditsVisible{
    padding-top: 1%;
    padding-bottom: 1%;
    background-color: #023E8A;
    box-shadow: 0 0 10px 0px #023E8A;
}
a, a:visited{
    color: #CAF0F8;
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