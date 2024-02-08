<template>
    <div class="selection">
        <ButtonRow
        :buttonsData="buttons"
        @clicked="SetActiveSection">
        </ButtonRow>
    </div>
    <component :is="activeSection"></component>
</template>
<script>
//Components
import ButtonRow from '@/components/ButtonRow.vue';
export default
{
    components: { ButtonRow },
    props: {
        buttons: {
            type: Array,
            required: true,
            default: ()=> []
        }
    },
    data() {
        return {
            activeSection: ''
        };
    },
    methods: {
        SetActiveSection(section) {
            this.activeSection = section;
        }
    },
}
</script>
<style scoped>
.selection{
    display: grid;
    grid-auto-flow: column;
    justify-self: center;
    height: max-content;
    gap: 10px;
    margin-top: 1%;
    margin-bottom: 1%;
}
</style>