<template>
    <div class="_horizontal-scroll">
        <slot>
            <v-autocomplete
  clearable
  dense
  filled
  rounded
  solo
></v-autocomplete>
        </slot>
    </div>
</template>

<script>
export default {
    mounted() {
        const content = this.$el;
        //Firefox
        if(content.addEventListener){
            content.addEventListener('DOMMouseScroll', function(e){
            content.scrollBy(-e.wheelDelta, 0);
            }, false);
        }
        //IE
        if(content.attachEvent){
            content.attachEvent('onmousewheel', function(e){
            content.scrollBy(-e.wheelDelta, 0);
            });
        }
        //Chrome
        content.onmousewheel = function(e){
            content.scrollBy(-e.wheelDelta, 0);
        }
    }
}
</script>

<style scoped>
._horizontal-scroll {
    box-sizing: border-box;
    overflow-x: scroll;
    overflow-y: hidden;
    text-align: left;
    white-space: nowrap;
}
</style>