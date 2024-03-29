<script>
export default {
    props: ['items', 'activeIndex']
}
</script>

<template>
    <div class="tags-list">
        <div
            v-for="(item, index) in items"
            @click="$emit('onItemClick', item)"
            :class="{'isActive': activeIndex.includes(item), 'tag-item': true}"
        >
            <span>{{ item }}</span>
        </div>

    </div>
</template>

<style scoped>

</style>
