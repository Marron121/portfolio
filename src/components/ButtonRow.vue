<template>
    <div class="selection">
        <ButtonWithIcon v-for="data in buttonsData" @selectComponent="onClick"
            :text="data.name"
            :icon="data.icon"
            :component="data.component"
            >
        </ButtonWithIcon>
    </div>
</template>
<script>
import ButtonWithIcon from '@/components/ButtonWithIcon.vue';
export default {
    components: { ButtonWithIcon },
    emits: ['clicked'],
    props: {
        buttonsData: {
            type: Array,
            required: true,
            default: ()=> []
        }
    },
    methods: {
        onClick(component){
            this.$emit('clicked',component);
        }
    }
}
</script>
<style scoped>
.selection{
    display: grid;
    grid-auto-flow: column;
    justify-self: center;
    height: max-content;
    gap: 100px;
}
</style>