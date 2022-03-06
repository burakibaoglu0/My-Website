//Burak İbaoğlu Dark Mode Component

<template>
    <div class="home">
        <div>
        <div @click="changeMode('light-to-dark')" v-if="!isDarkMode">
            <bi-icon icon-name="lightbulb-off-outline" color="#1d1d1d" size="20px"></bi-icon>
        </div>
        <div @click="changeMode('dark-to-light')" v-else>
            <BiIcon color="#fafafa" iconName="lightbulb-outline" size="20px" />
        </div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue';
import {COLOR_PALETTE} from "@/scss/variables";
import BiIcon from '@/components/generic_components/bi-icon.vue';

export default Vue.extend({
    components:{
        BiIcon
    },
    data() {
        return {
            isDarkMode: Boolean as any,
        };
    },
    mounted(){
        if (localStorage.getItem('isDarkMode') === null) {
            localStorage.setItem('isDarkMode', 'false');
        }
        if (localStorage.getItem('isDarkMode') === 'true') {
            this.isDarkMode = true;
            document.documentElement.style.backgroundColor = COLOR_PALETTE.DARK_MODE_BGC;
            document.documentElement.style.color = COLOR_PALETTE.DARK_MODE_COLOR;
        } else {
            this.isDarkMode = false;
            document.documentElement.style.backgroundColor = COLOR_PALETTE.LIGTH_MODE_BGC;
            document.documentElement.style.color = COLOR_PALETTE.LIGTH_MODE_COLOR;
        }
    },
    destroyed(){
        localStorage.removeItem('isDarkMode');
    },
    methods: {
        changeMode(mode: string) {
            if (mode === 'light-to-dark') {
                this.isDarkMode = true;
                localStorage.setItem('isDarkMode', 'true');
                document.documentElement.style.backgroundColor = COLOR_PALETTE.DARK_MODE_BGC;
                document.documentElement.style.color = COLOR_PALETTE.DARK_MODE_COLOR;
            } else {
                this.isDarkMode = false;
                localStorage.setItem('isDarkMode', 'false');
                document.documentElement.style.backgroundColor = COLOR_PALETTE.LIGTH_MODE_BGC;
                document.documentElement.style.color = COLOR_PALETTE.LIGTH_MODE_COLOR;
            }
        }
    }
})

</script>

<style>

</style>