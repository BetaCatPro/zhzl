<template>
    <div class="dropdown" ref="dropdownRef">
        <a href="#" class="btn btn-outline-light my-2 dropdown-toggle" @click.prevent="toggleOpen">
            {{props.title}}
        </a>
        <ul class="dropdown-menu" :style="{display: 'block'}" v-if="isOpen">
            <slot></slot>
        </ul>
    </div>
</template>

<script lang="ts" setup name="Dropdown">
import { defineProps, ref, watch } from 'vue'
import useClickOutside from '@/hooks/useClickOutside'

const props = defineProps({
    title: {
        type: String,
        required: true
    }
})

const isOpen = ref(false)
const dropdownRef = ref<null | HTMLElement>(null)
const toggleOpen = () => {
    isOpen.value = !isOpen.value
}
const isClickOutside = useClickOutside(dropdownRef)

watch(isClickOutside, () => {
    if (isOpen.value && isClickOutside.value) {
        isOpen.value = false
    }
})

</script>
