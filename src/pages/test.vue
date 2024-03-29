<script>
import Form from "@/components/notes/Form.vue";
import Notes from "@/components/notes/Notes.vue";
export default {
    name: "test",
    components: {Notes, Form},
    data(){
        return{
            input: {
              value: ''
            },
            notes: [
                {
                    title: 'Сделать дз',
                    tags: ['work', 'homework']
                }
            ],
        }
    },
    methods: {
        onSubmit(note){
            this.notes.push(note)
        },
        remove(index){
            this.notes.splice(index, 1)
        }
    },
    watch: {
        notes: {
            handler(updatedList) {
                localStorage.setItem("notes", JSON.stringify(updatedList));
            },
            deep: true,
        },
    },
    mounted() {
        const localNotes = localStorage.getItem("notes");
        if (localNotes) {
            this.notes = JSON.parse(localNotes);
        }
    }

}
</script>

<template>
    <div class="view-sm isCenter">

        <Form @onSubmit="onSubmit"/>

        <Notes :notes="notes" @remove="remove"/>
    </div>
</template>


<style lang="scss">
.note-form__wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
}
.note-form {
    display: flex;
    flex-direction: column;
    width: 100%;
    textarea {
        margin-bottom: 0;
    }
}
</style>
<style lang="scss">
.tags-list {
    padding: 10px 0;
    display: flex;
    justify-content: center;
}
.tag-item {
    padding: 8px 22px;
    margin-right: 10px;
    background-color: #fff;
    border-radius: 22px;
    user-select: none;
    cursor: pointer;
    &.isActive {
        background-color: #444ce0;
        color: #fff;
    }
    &.isPreview {
        padding: 0;
        color: #444ce0;
        cursor: default;
        &:before {
            content: '#';
        }
    }
    &:last-child {
        margin-right: 0;
    }
}
</style>
