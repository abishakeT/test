
<template>
    <div>
        <canvas ref="fabricCanvas" :width="canvasWidth" :height="canvasHeight"></canvas>
        <button @click="addRectangle">Add Rectangle</button>
    </div>
</template>

<script>
import { Canvas, Rect } from 'fabric';
import { ref } from 'vue';

const fills = ref(["red", "yelow", "green", "blue", "purple"])
const fill = () => Math.random(fills.value)
console.log(fill)
export default {
    data() {
        return {
            canvas: null,
            canvasWidth: 500,
            canvasHeight: 400,
        };
    },
    mounted() {
        // init fabric
        this.canvas = new Canvas(this.$refs.fabricCanvas);

        this.canvas.on('object:selected', (e) => {
            console.log('Object selected:', e.target);
        });
    },
    methods: {
        addRectangle() {
            // Add a rectangle to the canvas
            const rect = new Rect({
                left: 100,
                top: 100,
                fill: fill,
                width: 200,
                height: 100,

            });
            this.canvas.add(rect);
        },
    },
};
</script>

<style scoped>
canvas {
    border: 1px solid black;
}
</style>
