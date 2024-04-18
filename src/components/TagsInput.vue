<template>

    <div v-for="(tag, index) in tags">{{ index + ":" + tag }}</div>
    <input type="text" v-bind:value="newTag" />
</template>


<script>
export default {
    data: () => ({
        tags: ["Vue", "React", "Angular", "Next"],
        newTag: "preact"
    })
}    
</script>