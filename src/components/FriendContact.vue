<template>
    <li>
        <h2>{{ name }} {{isFavourite === true ?'(Favourite)': ''}}</h2>
        <button @click="toggleFavourite">Toggle Favourite</button>
        <button @click="toggleDetails">{{detailsAreVisible ? 'Show' : 'Hide'}} Details</button>
        <ul v-if="detailsAreVisible">
            <li><strong>Phone:</strong>{{ phoneNumber }}</li>
            <li><strong>Email:</strong> {{ emailAddress }}</li>
        </ul>
        <button @click="$emit('delete', id)">Delete</button>
    </li>
</template>

<script>
export default {
    props: {
        id:{
            type: String,
            required: true
        },
        name: {
            type: String,
            required: true,
        },
        phoneNumber: {
            type: String,
            required: true
            },
        emailAddress: {
            type: String,
            required: true,
        },
        isFavourite: {
            trpe: Boolean,
            required: true,
            default: false,
        },
    },

    emits: ['toggle-favourite', 'delete'],
    // emits: {
    //     'toggle-favourite': function(id){
    //         if(id){
    //             true
    //         }else{
    //             console.warn('Id is missing!')
    //             return false;
    //         }
    //     }
    // },
    data() {
        return {
            detailsAreVisible: true,
        }
    },
    methods: {
        toggleDetails(){
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFavourite(){
            this.$emit('toggle-favourite', this.id);
        }
    },
};
</script>
