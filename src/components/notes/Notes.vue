<script>
export default {
    props: ['notes'],
    methods: {
        remove(index){
            this.$emit('remove', index)
        }
    }
}
</script>

<template>
    <div class="notes-list">
        <div class="note-item" v-for="(note, index) in notes">
            <div class="note-header">
                <p>{{ note.title }}</p>
            </div>

            <div class="tags-list">
                <div class="tag-item isPreview " v-for="tag in note.tags">
                    <span>{{tag}}</span>
                </div
            ></div>

            <div style="display: flex; gap: 10px;flex-direction: row-reverse;">
                <button class="btn btnDanger" @click="remove(index)" >Удалить</button>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
.notes-list {
    padding: 40px 0;
}
.note-item {
    width: 100%;
    padding: 18px 20px;
    margin-bottom: 20px;
    border-radius: 14px;
    background-color: #ffffff;
    transition: all 0.25s cubic-bezier(0.02, 0.01, 0.47, 1);
    box-shadow: 0 30px 30px rgba(0, 0, 0, 0.02);
    &:hover {
        box-shadow: 0 30px 30px rgba(0, 0, 0, 0.04);
        transform: translate(0, -6px);
        transition-delay: 0s !important;
    }
}
.note-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.note-footer {
    display: flex;
    flex-direction: column;
    justify-content: start;
    align-items: start;
}
</style>
