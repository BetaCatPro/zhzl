<template>
    <teleport to="#back">
        <div
            class="d-flex justify-content-center align-items-center h-100 w-100 loading-container"
            :style="{backgroundColor: props.background || ''}"
        >
            <div class="loading-content">
                <div class="spinner-border text-primary" role="status">
                    <span class="sr-only">{{ props.text || 'loading'}}</span>
                </div>
                <p v-if="text" class="text-primary small">{{props.text}}</p>
            </div>
        </div>
    </teleport>
</template>

<script lang="ts" setup name="Loader">
import { defineProps, onUnmounted } from 'vue'

const props = defineProps({
    text: {
        type: String
    },
    background: {
        type: String
    }
})

const node = document.createElement('div')
node.id = 'back'
document.body.appendChild(node)
onUnmounted(() => {
    document.body.removeChild(node)
})
</script>

<style>
.loading-container {
    background: rgba(255, 255, 255, .5);
    z-index: 100;
    position: fixed;
    top: 0;
    left: 0;
}

.loading-container {
    text-align: center;
}
</style>
