<template>
    <div class="new-note">
        <label>Title</label>
        <input type="text" v-model="note.title">
        <label>Description</label>
        <textarea v-model="note.descr"></textarea>
        <button class="btn btnPrimary" @click="addNote">New Note</button>
    </div>
</template>

<script>
    export default {
        name: "NewNote",
        props: {
            note: {
                type: Object,
                required: true,
            }
        },
        methods: {
            addNote() {
                this.$emit('addNote', this.note)
            }
        }
    }
</script>

<style scoped>
    .new-note {
        text-align: center;
    }
    button {
        margin-top: 1rem;
    }

</style>