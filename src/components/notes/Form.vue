<script>
import TagList from "@/UI/TagList.vue";
export default {
    data(){
        return{
            value: '',
            tags: ["work", "travel", "home"],
            activeNotes: []

        }
    },
    methods: {
        onSubmit(){
            const note = {
                title: this.value,
                tags: this.activeNotes
            }
            this.$emit('onSubmit', note)
            this.value = ''
            this.activeNotes = []
        },
        onItemClick(item){
            if(this.activeNotes.includes(item)){
                this.activeNotes.splice(this.activeNotes.indexOf(item), 1);
            }else {
                this.activeNotes.push(item);
            }



        }

    },
    components: {TagList}
}
</script>

<template>
    <form @submit.prevent="onSubmit" class="note-form">
        <textarea v-model="value"  placeholder="Write note" required></textarea>
        <TagList :items="tags" @onItemClick="onItemClick" :activeIndex="activeNotes"/>

        <button class="btn btnPrimary" type="submit">Создать</button>
    </form>
</template>

<style scoped>

</style>
