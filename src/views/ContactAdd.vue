<template>
    <div class="page">
        <h4>Thêm Liên Hệ</h4>
        <ContactForm :contact="contact" @submit:contact="addContact" />
    </div>
</template>

<script>
import ContactForm from '@/components/ContactForm.vue';
import ContactService from '@/services/contact.service';

export default {
    components: { ContactForm },
    data() {
        return {
            contact: {
                name: "",
                email: "",
                address: "",
                phone: "",
                favorite: false,
            },
        };
    },
    methods: {
        async addContact(data) {
            await ContactService.create(data);
            this.$router.push({ name: "contactbook" });
        },
    },
};
</script>