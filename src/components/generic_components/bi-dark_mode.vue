//Burak İbaoğlu Dark Mode Component

<template>
    <div class="home">
        <div>
        <div class="icons" @click="changeMode('light-to-dark')" v-if="!isDarkMode">
            <bi-icon icon-name="lightbulb-off-outline" color="#1d1d1d" size="1vw"></bi-icon>
            Lights Off
        </div>
        <div class="icons" @click="changeMode('dark-to-light')" v-else>
            <BiIcon color="#fafafa" iconName="lightbulb-outline" size="1vw" />
            Lights On
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
            this.$store.state.darkMode = false;
            
        }
        if (localStorage.getItem('isDarkMode') === 'true') {
            this.isDarkMode = true;
            this.$store.state.darkMode = true;
            document.documentElement.style.backgroundColor = COLOR_PALETTE.DARK_MODE_BGC;
            document.documentElement.style.color = COLOR_PALETTE.DARK_MODE_COLOR;
        } else {
            this.isDarkMode = false;
            this.$store.state.darkMode = false;
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
                this.$store.state.darkMode = true;
                localStorage.setItem('isDarkMode', 'true');
                document.documentElement.style.backgroundColor = COLOR_PALETTE.DARK_MODE_BGC;
                document.documentElement.style.color = COLOR_PALETTE.DARK_MODE_COLOR;
            } else {
                this.isDarkMode = false;
                this.$store.state.darkMode = false;
                localStorage.setItem('isDarkMode', 'false');
                document.documentElement.style.backgroundColor = COLOR_PALETTE.LIGTH_MODE_BGC;
                document.documentElement.style.color = COLOR_PALETTE.LIGTH_MODE_COLOR;
            }
        }
    }
})

</script>

<style lang="scss">

@import "@/scss/index.scss";

.icons{
    @include flex-container(row, center, center, nowrap);
    cursor: pointer;
    flex: 0 0 auto;
    gap: .4vw;
    font-size: .8vw;
}

</style>