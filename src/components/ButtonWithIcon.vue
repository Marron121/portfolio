<template>
    <div class="insideButton" v-on:click="clickedButton()">
        <img v-bind:src=icon class="insideButton-icon"/> <div class="insideButton-text">{{ text }}</div>
    </div>
</template>
<script>
export default{
    emits: ['selectComponent'],
    props: {
        text: {
            type: String,
            required: true,
            default: ""
        },
        icon : {
            type: String,
            required: true
        },
        url: {
            type: String,
            required: false,
            default: ''
        },
        component: {
            required : false,
        }
    },
    methods: {
        clickedButton(){
            if (this.url != ''){
                window.open(this.url, '_blank', 'noreferrer');
            }
            else{
                this.$emit('selectComponent', this.component);
            }
        },
    }
}
</script>
<style scoped>
.insideButton{
    display: grid;
    padding: auto;
    grid-template-columns: 100px 1fr;
    align-items: center;
    background-color: #0096C7;
    border-color: #0096C7;
    min-height: max-content;
    min-width: fit-content;
    width: fit-content;
    cursor: pointer;
    padding-left: 15px;
    padding-right: 15px;
    border-radius: 5px;
    transition: 0.5s;
}
.insideButton:hover{
    background-color: #0077B6;
    border-color: #0077B6;
    box-shadow: 0 0 20px 0px #0077B6;
}
.insideButton-icon{
    min-width: 50px;
    min-height: 50px;
    max-width: 100px;
    max-height: 100px;
    padding-left: 10px;
    padding-right: 10px;
}
.insideButton-text{
    color: black;
    font-weight: bolder;
}
</style>