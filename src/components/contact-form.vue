<template>
    <div id="contact-form">
        <form class="vue-form" @submit.prevent="submit">
            <div>
                <h2>Name</h2>
                <input v-model="name">
            </div>
            <div>
                <h2>Email</h2>
                <input v-model="email">
            </div>
            <div>
                <h2>Phone (optional)</h2>
                <input v-model="phone">
            </div>
            <div>
                <h2>Subject</h2>
                <input v-model="subject">
            </div>
            <div>
                <h2>Description</h2>
                <textarea v-model="description" cols="40" rows="5"></textarea>
            </div>
            <div v-if="!sent">
                <input id="button-send" type="submit" value="Verzenden">
            </div>
            <div v-if="sent">
                <p>Uw bericht verzonden</p>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    name: "contact-form",
    data() {
        return {
            name: '',
            email: '',
            phone: '',
            subject: '',
            description: '',
            sent: false,
        };
    },
    methods: {
        submit: function () {
            let form = {};
            form.name = this.name;
            form.subject = this.subject;
            form.email = this.email;
            form.phone = this.phone;
            form.message = this.description;
            axios({
                url: '/mail.php',
                method: "POST",
                data: form
            }).then(() => {
                this.sent = true;
            });
        },
    },

};
</script>

<style scoped>
#contact-form {
    width: 67.5%;
    margin: auto;

    div {
        margin: 12px 0;
    }

    input,
    textarea {
        font-size: 1.5rem;
        width: 100%;
        height: 4vh;
        background: black;
        border-radius: 6px;
        color: darkcyan;
    }

    textarea {
        height: 28vh;
    }

    #button-send {
        height: 64px;
        cursor: pointer;
        border-radius: 20px;
    }

    #button-send:hover {
        border-color: white;
        transition: border-color 0.25s linear;
    }
}

h2 {
    margin: 0;
    font-size: 1.8rem;
}

p {
    width: 70%;
    margin: 6px 0;
    text-align: left;
}
</style>