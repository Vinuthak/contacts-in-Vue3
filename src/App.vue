<template>
    <div class="bg-black text pt-3" :style="{ height: '100vh' }">
        <h1 class="text-center text-success">ContactOpedia</h1>
        <div class="container">
            <div class="row text-white p-2 mb-2">
                <div class="col-6">Owner Name : <input type="text" v-model="ownerName"/></div>
                <div class="col-6">Lucky Number : <input type="text" v-model.number="maxNumber"/></div>
            </div>
            <br><br>

            <div>
                <AddContact @add-contact="addToContacts($event)"></AddContact>
            </div>
            <div class="row">
                <div class="col-12" v-for="contact in contacts" :key="contact.name">
                    <contact 
                        :name= "contact.name" 
                        :phone="contact.phone" 
                        email="foo@bar.com"
                        :ownerName="ownerName"
                        :isFavorite="contact.isFavorite"
                        @update-favorite="contact.isFavorite = onUpdateFavorite($event,contact.name)"
                        >
                    </contact>
                </div>
            </div>
        </div>
    </div>
</template>


<script setup>
    import Contact from './components/Contact.vue';
    import AddContact from './components/AddContact.vue';
    import { ref, reactive, provide } from 'vue';

    const ownerName = ref("abcd_z");

    const maxNumber = ref(100);
    provide('maxLuckyNumber', maxNumber);

    const contacts = reactive([
        {
            name: "JayRam",
            phone: 11111,
            ownerName: ownerName,
            isFavorite: false
        },
        {
            name: "MohanLal",
            phone: 22222,
            ownerName: ownerName,
            isFavorite: true
        },
        // {
        //     name: "NTR",
        //     phone: 33333,
        //     ownerName: ownerName,
        //     isFavorite: true
        // },
        // {
        //     name: "RamCharan",
        //     phone: 44444,
        //     ownerName: ownerName,
        //     isFavorite: false
        // }
    ])
    function onUpdateFavorite(oldValueFromChildComponent,contactNameFromParent){
        console.log(oldValueFromChildComponent);
        console.log(contactNameFromParent);
        return  !oldValueFromChildComponent.isFavorite;
         
    }

    function addToContacts(contact){
        contact.ownerName = ownerName.value;
        contact.isFavorite = false;
        console.log(contact);
        contacts.push(contact);
        console.log(contacts);
    }
</script>

<style></style>