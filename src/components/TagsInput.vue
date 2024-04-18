<template>

    <div v-for="(tag, index) in tags" :key="index">
        {{ index + ":" + tag }}
        <a v-on:click.prevent="removeTag(index)" href="#">&times;</a>
    </div>

    <hr />
    {{ newTag }}

    <input type="text" v-model.trim="newTag" v-on:keydown.enter="addNewTag" v-on:keydown.delete="removeLastTag"
        v-on:keydown.tab.prevent="addNewTag" v-bind:class="{ 'tag-exists': tags.includes(newTag) }" />
</template>


<script>
export default {
    data: () => ({
        tags: ["Vue", "React", "Angular", "Next"],
        newTag: "preact"
    }),
    methods: {
        addNewTag() {

            if (this.newTag) {
                this.tags.push(this.newTag);
                this.newTag = "";
            }
        },
        removeTag(index) {
            this.tags.splice(index, 1);
        },
        removeLastTag() {
            if (this.newTag.length === 0) {
                this.removeTag(this.tags.length - 1);
            }
        }
    }
};    
</script>

<style scoped>
.tag-exists {
    color: red;
    text-decoration: line-through;
}
</style>