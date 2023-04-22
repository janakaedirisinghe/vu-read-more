<!-- =========================================================================================
    File Name: VReadMore.vue
    Description: Read More Component For Vue Applications
    Component Name: VReadMore
    ----------------------------------------------------------------------------------------
    Author: Janaka Edirisinghe with ♥
========================================================================================== -->
<template>
    <span>
        <span :style="textStyle">{{ text.slice(0, is_on_read_more ? text.length : charLength) || '' }}
            <span v-if="!is_on_read_more && text.length > charLength">...</span>
        </span>
        <span :style="buttonStyle" v-if="text.length > charLength" @click.stop="onClickButton">
            {{ is_on_read_more ? (readMoreOnly ? '' : readLessText) : readMoreText }}
        </span>
    </span>
</template>
  
<script>
export default {
    name: "VReadMore",
    data() {
        return {
            is_on_read_more: false
        }
    },
    props: {
        text: {
            type: String,
            default: ''
        },
        charLength: {
            type: Number,
            default: 20
        },
        readMoreText: {
            type: String,
            default: 'read more'
        },
        readLessText: {
            type: String,
            default: 'read less'
        },
        buttonStyle: {
            type: Object,
            default: function () { return { color: 'blue', cursor: 'pointer', 'text-decoration': 'underline' } }
        },
        textStyle: {
            type: Object,
            default: function () { return {} }
        },
        readMoreOnly: {
            type: Boolean,
            default: false
        },
        redirect: {
            type: Object,
            default: function () { return { link: '#', newTab: true } }
        }
    },
    methods: {
        onClickButton() {
            if (this.redirect.link !== '#' && !this.is_on_read_more) window.open(this.redirect.link, this.redirect.newTab ? '_blank' : '_self', 'noreferrer');
            this.is_on_read_more = !this.is_on_read_more;
        }
    },
}
</script>
  
<style scoped></style>
  