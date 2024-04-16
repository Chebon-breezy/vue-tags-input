<template>

    <div>{{ tags }}</div>
    <div>{{ tags.length }}</div>
    <input type="text" />
</template>


<script>
export default {
    data: () => ({
        tags: ["Vue", "React", "Angular", "Next"]
    })
}    
</script>