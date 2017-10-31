<template>
    <div id="toolbar">
        <i class="glyphicon glyphicon-plus" @click="addNote"></i>
        <i class="glyphicon glyphicon-star"
            @click="toggleFavorite"
            :class="{starred: activeNote.favorite}"
        ></i>
        <i class="glyphicon glyphicon-remove" @click="deleteNote"></i>
    </div>
</template>


<script>
    import {addNote, deleteNote, toggleFavorite} from '../vuex/actions'
    
    export default {
        vuex: {
            getters: {
                activeNote: state => state.activeNote
            },
            actions: {
                addNote,
                deleteNote,
                toggleFavorite
            }
        }
    }
</script>