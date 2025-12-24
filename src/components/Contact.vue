<template>
    <div class="bg-info rounded p-1 m-1 pb-4">
        <div class="row">
            <div class="col-6">
                <h3>Name: {{ name }}</h3>
                <p>Email: {{ email }}</p>
                <p>Phone Number: {{ phone }}</p>
                
            </div>           
            <div class="col-3">
                <button 
                    :class="[isFavorite ? 'btn btn-warning': 'btn btn-success']" 
                    @click=" 
                        emit(
                            'update-favorite',
                            { isFavorite: props.isFavorite, name: props.name }
                        )"
                >
                    {{ isFavorite ? 'Remove From Favourite' : 'Add to Favourite' }}
                </button>
            </div> 
            <div class="col-3">
                 <LuckyNumber></LuckyNumber>
            </div>
        </div>
        <span class="float-end small"   :v-if="ownerName != ''">Owner Name: {{ ownerName }}</span>
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    import LuckyNumber from './LuckyNumber.vue';

    const email = ref("example@gmail.com");
    const props = defineProps({ 
        name: {type:String, required:true},
        phone: Number,
        email: {type:String, required:false, default:"n/a"},
        ownerName:String,
        isFavorite:Boolean,
        });
    const emit = defineEmits(["update-favorite"]);
</script>