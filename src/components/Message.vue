<template>
    <div class="message">
        <p>{{ message }}</p>
    </div>
</template>

<script>
    export default {
        name: "Message",
        props: {
            message: {
                type: String,
                required: true,

            }
        }
    }
</script>

<style scoped>
.message {
    text-align: center;
    padding: 1rem;
    color: red;
}
</style>