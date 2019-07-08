<template>
    <div class="view">
        <div class="character-list" v-for="(char,i) in characters" :key="i">
            {{char.name}}
        </div>
    </div>
</template>

<script>
export default {
    name: 'ViewMore',
    data: function()    {
        return {
            characters: []
        }
    },
    props:  [resultData]
}
</script>

