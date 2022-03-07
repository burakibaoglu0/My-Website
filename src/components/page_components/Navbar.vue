<template>
    <div class="navbar-main">
        <div v-for="route in routes" :key="route.name" class="navbar-routes">
            <div class="route-icons">
                <BiIcon :iconName="route.iconName" :color="iconColor" size="1vw"/>
            </div>
            <div class="route-name">{{route.name}}</div>
        </div>
        <div class="change-color-mode">
            <BiDarkMode />
        </div>
    </div>
</template>

<script lang="ts">
    import BiDarkMode from "@/components/generic_components/bi-dark_mode.vue";
    import BiIcon from "@/components/generic_components/bi-icon.vue";
    export default {
        components: {
            BiDarkMode,
            BiIcon
        },
        props: {
            routes: {
                type: Array,
                required: true
            }
        },
        data() {
            return {
                iconColor: '#1d1d1d'
            };
        },
        mounted(){
            window.addEventListener('scroll', this.handleScroll);
        },
        methods: {
            handleScroll(){
                let element = document.querySelector('.navbar-main') as HTMLElement;
                if(window.scrollY > 300){
                    element.style.position = 'fixed';
                }
                else if(window.scrollY === 0){
                    element.style.position = 'relative';
                }
            },
        },
        watch: {
            '$store.state.darkMode': function (newVal: boolean) {
                this.iconColor = newVal ? '#fafafa' : '#1d1d1d';
            }
        }
    }
</script>

<style lang="scss">
    @import "@/scss/index.scss";

    $font-size: .8vw;

    .navbar-main {
        @include flex-container(row, center, space-evenly, nowrap);
        width: 100%;
        padding: 1vw 2vw;
        @include box-shadow(0px, 0px, 5px);
        flex:0 0 auto;
        position: relative;

        .navbar-routes {
            @include flex-container(row, center, center, nowrap);
            cursor: pointer;
            flex: 0 0 auto;
            gap: .4vw;
            font-size: $font-size;
            @include transition(all ease-in-out .2s);

            .route-icons {
                @include flex-container(column, center, center, nowrap);
                flex: 0 0 auto;
            }

            .route-name {
                @include flex-container(column, center, center, nowrap);
                flex: 0 0 auto;
            }

            &:hover {
                transform: scale(1.08);
            }
        }
    }
</style>