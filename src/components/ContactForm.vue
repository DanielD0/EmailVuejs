<template>
    <div class="container">
        <form ref="form" @submit.prevent="sendEmail">
            <label>Nombre</label>
            <input 
                type="text" 
                v-model="name"
                name="name"
                placeholder="Your Name"
            >
            <label>Email</label>
            <input 
                type="email" 
                v-model="email"
                name="email"
                placeholder="Your Email"
                >
            <label>Mensaje</label>
            <textarea 
                name="message"
                v-model="message"
                cols="30" rows="5"
                placeholder="Message">
            </textarea>
            <input type="submit" value="Send">
        </form>
        <button @click="enviarmail">Enviar Correo</button>
    </div>
</template>
<script>
import emailjs from 'emailjs-com';
export default {
    name: 'ContactUs',
    data() {
        return {
        name: '',
        email: '',
        message: ''
        }
    },
    methods: {
        sendEmail() {
        try {
            emailjs.sendForm('service_fz1bids', 'template_vqxhfnc', this.$refs.form,
            '9fpbftQsmZF8p7Q7y', {
            name: this.name,
            email: this.email,
            message: this.message
        })
        } catch(error) {
            console.log({error})
        }
        // Reset form field
        this.name = ''
        this.email = ''
        this.message = ''
        },
        enviarmail(){
            try {
            emailjs.sendForm('service_fz1bids', 'template_j1cguyf',this.$refs.form,'9fpbftQsmZF8p7Q7y')
            console.log('se envio de manera correcta')
            } catch(error) {
                console.log({error})
            }
        }
    }
}
</script>
<style scoped>
* {box-sizing: border-box;}

.container {
    display: block;
    margin:auto;
    text-align: center;
    border-radius: 5px;
    background-color: #f2f2f2;
    padding: 20px;
    width: 50%;
}

label {
    float: left;
}

input[type=text], [type=email], textarea {
    width: 100%;
    padding: 12px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
    margin-top: 6px;
    margin-bottom: 16px;
    resize: vertical;
}

input[type=submit] {
    background-color: #4CAF50;
    color: white;
    padding: 12px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

input[type=submit]:hover {
    background-color: #45a049;
}

button{
    background-color: #4CAF50;
    color: white;
    padding: 12px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
}
</style>