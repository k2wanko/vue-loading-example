<template>
    <div class="loading-container">
        <transition name="fade" key="loading">
            <div v-if="loading" class="loading">
                <pulse-loader></pulse-loader>
            </div>
            <div v-else key="loaded" class="loaded">
                <slot></slot>
            </div>
        </transition>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Component from 'vue-class-component'
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'

@Component({
    props: {
        loading: Boolean
    },
    components: { PulseLoader }
})
export default class LoadingConatiner extends Vue {
}
</script>

<style>
.loading-container {
    position: relative;
}

.loading-container .loading {
    position: fixed;
    z-index: 1000;
    left: 0;
    right: 0;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s
}

.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0
}
</style>