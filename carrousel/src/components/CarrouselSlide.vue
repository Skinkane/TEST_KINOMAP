<template>
    <transition name="slide">
        <div v-show="visible">
            <slot></slot>
        </div>
    </transition>
</template>

<script>
export default {
    data () {
        return {
            index: 0
        }
    },

    computed: {
        visible() {
            return this.index === this.$parent.index
        }
    }
}
</script>

<style>

.slide-enter-active{
    animation: slideIn 2s;
}

.slide-leave-active{
    animation: slideOut 2s;
    position: absolute;
    top: 0;
    left: 0;
}

@keyframes slideIn {
    from {transform: translateX(100%); }
    to {transform: translateX(0); }
}

@keyframes slideOut {
    from {transform: translateX(250%); }
    to {transform: translateX(-100%); }
}
</style>