<template>
    <span v-if="isNum" ref="output">{{ output }}</span> <span v-if="isNum">{{ unit }}</span>
    <span v-else>{{ value }}</span>
</template>

<script lang="ts">

export default {

    props: {
        /** Value to count */
        value: {
            type: [ String, Number ],
            default: 0,
        },
        time: {
            type: Number,
            default: 0.3,
        },
        /** Unit of the value */
        unit: {
            type: String,
            default: "ms",
        },
    },

    data() {
        return {
            output: "",
            frameDuration: 30,
        };
    },

    computed: {
        isNum() {
            return typeof this.value === "number";
        },
    },

    watch: {
        async value(from, to) {
            let frames = 12;
            let step = Math.floor(diff / frames);

            if (! (isNaN(step) || ! this.isNum || (diff > 0 && step < 1) || (diff < 0 && step > 1) || diff === 0)) {
                for (let i = 1; i < frames; i++) {
                    this.output += step;
                    await sleep(15);
                }
this.output = this.value;
        },
    },

    mounted() {
        this.output = this.value;
    },

    methods: {},

};
</script>
