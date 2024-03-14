<template>
    <div class="Footer">
        <div class="Footer-separator"></div>
        <div class="Footer-grid">
            <p><span class="bold">Contact:</span> <a href="mailto:aaronmigo2.0@gmail.com">aaronmigo2.0@gmail.com</a></p>
            <div class="Footer-ThemeButton" v-on:click="ChangeTheme()">{{themeMessage}}</div>
            <div class="Footer-socialmedia">
                <a href="https://www.linkedin.com/in/aaron-miranda-g%C3%B3mez-886310251/" target="_blank"><img v-bind:src="images[0]" alt="Linkedin"></a>
                <a href="https://github.com/Marron121" target="_blank"><img v-bind:src="images[1]" alt="Github"></a>
                <a href="https://marron121.itch.io/" target="_blank"><img v-bind:src="images[2]" alt="Itchio"></a>
                <a href="https://gamedev.lgbt/@Marron121" target="_blank"><img v-bind:src="images[3]" alt="Mastodon"></a>
            </div>
        </div>
    </div>
</template>
<script>
//Images
import GithubIcon from '@/assets/icons/github.svg';
import ItchioIcon from '@/assets/icons/itchio.svg';
import MastodonIcon from '@/assets/icons/mastodon.svg';
import LinkedinIcon from '@/assets/icons/linkedin.svg';
export default{
    data(){
        return{
            images: [LinkedinIcon, GithubIcon, ItchioIcon, MastodonIcon],
            currentColorScheme: "",
            themeMessage: "Change to /theme/ mode /icon/"
        }

    },
    created(){
            this.currentColorScheme = getComputedStyle(document.documentElement).getPropertyValue('--color-scheme-os');
            this.setTheme();
        },
    methods: {
        ChangeTheme(){
            this.currentColorScheme = this.currentColorScheme == 'dark'? 'light' : 'dark';
            this.setTheme();
        },
        setTheme(){
            if (this.currentColorScheme == 'dark')
            {
                this.themeMessage = "Change to light mode 🌞";
            }
            else
            {
                this.themeMessage = "Change to dark mode 🌙";
            }
            document.documentElement.className = this.currentColorScheme;
        }
    }
}
</script>
<style scoped>
.Footer{
    position: fixed;
    width: 100%;
    min-height: 60px;
    height: 75px;
    left: 0;
    bottom: 0;
    padding-bottom: 1%;
    background-color: var(--color-footer);
}
.Footer-grid{
    display: grid;
    grid-template-rows: 1fr 3fr;
    align-items: left;
    justify-items: left;
    width: 100%;
    padding: 0.5%;
}
.Footer-ThemeButton{
    position: absolute;
    right: 10%;
    width: fit-content;
    height: fit-content;
    color: var(--color-text);
    background-color: var(--color-background);
    padding: 1%;
    border-style: solid;
    border-color: var(--color-background);
    border-radius: 10%;
    transition: all 0.5s;
}
.Footer-ThemeButton:hover{
    box-shadow: 0 0 15px 0px var(--color-background);
}
.Footer-socialmedia{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    column-gap: 25%;
    justify-self: left;

}
.Footer-separator{
    max-width: 100%;
    min-height: 5px;
    height: 5px;
    background-color: var(--color-footer-separator);
}
img{
    width: 32px;
    max-width: 32px;
    height: auto;
    max-height: auto;
    object-fit: scale-down;
}
</style>

