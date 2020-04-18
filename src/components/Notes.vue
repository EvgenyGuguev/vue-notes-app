<template>
    <div class="notes">
        <div class="note" :class=" {full: !grid }" v-for="(note, index) in notes" :key="index">
            <div class="note-header" :class=" {full: !grid }">
                <p>{{ note.title }}</p>
                <p style="cursor: pointer" @click="removeNote(index)">x</p>
            </div>
            <div class="note-body">
                <p>{{ note.descr }}</p>
                <span>{{ note.date }}</span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Notes",
        props: {
            notes: {
                type: Array,
                required: true,
            },
            grid: {
                type: Boolean,
                required: true,
            },
        },
        methods: {
            removeNote(index) {
                console.log(`Note id - ${index} removed`);
                this.$emit('remove', index);
            }
        }
    }
</script>

<style lang="scss" scoped>
    .notes {
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
        padding: 1rem 0;
    }
    .note {
        width: 48%;
        padding: 1rem 1rem;
        margin-bottom: 2rem;
        background-color: white;
        transition: all .25s cubic-bezier(.02,.01,.47,1);
        box-shadow: 0 30px 30px rgba(0,0,0,.02);
        &:hover {
            box-shadow: 0 30px 30px rgba(0, 0, 0, .04);
            transform: translate(0, -6px);
            transition-delay: 0s !important;
        }
        &.full {
            width: 100%;
            text-align: center;
        }
    }

    .note-header {
        display: flex;
        justify-content: space-between;
        &.full {
            justify-content: center;
            p {
                margin-right: 1rem;
                &:last-child {
                    margin-right: 0;
                }
            }
        }
    }

    .note-header p {
        color: #444ce0;
        font-size: 1rem;
    }
    .note-body p {
        margin: 1rem 0;
    }
    .note-body span {
        font-size: 0.7rem;
        color: #999999;
    }
</style>