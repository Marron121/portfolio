<template>
    <h2>Video Editing</h2>
    <p>I've worked in the edition, compilation and upload of various videos, including trailers and showreels, with the use of tools like <span class="bold">Sony Vegas</span>, <span class="bold">Kdenlive</span> and more.</p>
    <div class="videoHolder">
        <video controls>
            <source :src="videos[0]" type="video/mp4">
        Trailer for the videogame A Story Told By The Stars
        </video>
        <video controls>
            <source :src="videos[1]" type="video/mp4">
        Trailer for the videogame Cybershooter
        </video>
    </div>
</template>
<script>
//Videos
import astbts_trailer from '@/assets/videos/trailer_astbts.mp4';
import cybershooter_trailer from '@/assets/videos/cybershooter_trailer_finalv4.mp4';
export default{
    data(){
        return{
            videos: [astbts_trailer, cybershooter_trailer]
        }
    }
}
</script>
<style>
.videoHolder{
    align-self: center;
    align-content: center;
    justify-self: center;
    justify-content: center;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    min-width: 80%;
    width: 80%;
    gap: 1%;
    padding: 1%;
    margin-top: 1%;
    border-style: solid;
    border-color: #023E8A;
    transition: all 0.5s;
}
.videoHolder:hover{
    box-shadow: 0 0 10px 5px #023E8A;
}
video {
    width: 100%;
    height: auto;
    object-fit: scale-down;
}
</style>