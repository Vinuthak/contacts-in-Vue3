<template> 
    <div class="container border rounded p-2">
        <div class="text-center text-white">Add Contact</div>
        
        <form @submit.prevent="preventSubmit()">
            <div class="row">
                <div class="col-4">
                    <input type="text" class="form-control" v-model="contact.name" placeholder="Name"/>
                </div>
                <div class="col-4">
                    <input type="text" class="form-control" v-model.number="contact.phone" placeholder="Phone"/>
                </div>
                <div class="col-4">
                    <input type="text" class="form-control" v-model="contact.email" placeholder="Email"/>
                </div>
            </div>
            <div class="col-6 offset-3 p-2">
                <button 
                    type="submit" 
                    class="btn btn-secondary w-100" 
                >
                    Add Contact
                </button>
            </div>
        </form>

    </div>
</template>

<script setup>
    import { reactive, defineProps } from 'vue';

    const contact = reactive({
        name: "",
        phone: "",
        email: "",
    });

    const props = defineProps({
        addToContacts: Function
    })
    
    function preventSubmit(){
        props.addToContacts(contact);
    }
</script>