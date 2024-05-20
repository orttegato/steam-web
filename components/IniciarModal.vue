<template v-show="iniciarmodalActive" >
    <div class="panel">
        <form @submit.prevent="submitForm">
            <h1>Iniciar sesión</h1>
            <div class="middle-modal">
                <div>
                    <label for="name">
                        <p>Nombre de usuario:</p>
                    </label>
                    <input class="input" type="text" v-model="formData.name" id="name"
                        placeholder="Introduce tu nombre de usuario" />
                </div>

                <div>
                    <label for="password">
                        <p>Contraseña:</p>
                    </label>
                    <input class="input" type="password" v-model="formData.password" id="password"
                        placeholder="Introduce tu contraseña" />
                    <p class="olvido">¿Has olvidado tu contraseña?</p>
                </div>
            </div>

            <div class="boton-modal">
                <BaseButton type="submit">Iniciar sesión</BaseButton>
                <button @click.prevent="handleCancel">
                    <p>Cancelar</p>
                </button>
            </div>
        </form>
    </div>

    <div class="aux" v-show="!iniciarmodalActive">
        <p>¿No tienes cuenta?</p>
        <p><b @click="openRegistrationModal">Regístrate aquí</b></p>
    </div>

    <RegistrationModal v-if="registrationModalActive" @close-modal="closeRegistrationModal" />


</template>


<script setup>

import { ref } from 'vue'
import RegistrationModal from './RegistrationModal.vue';

const emit = defineEmits(["closeModal",])
const formData = ref({
    name: '',
    password: ''
})

const iniciarmodalActive = ref(false);
const registrationModalActive = ref(false);


const openRegistrationModal = () => {
    iniciarmodalActive.value = false;
}

const closeRegistrationModal = () => {
    registrationModalActive.value = false;
}

const submitForm = async () => {
    // Verificar las credenciales localmente (simulado)
    if (formData.value.name === 'usuario' && formData.value.password === 'contraseña') {
        // Credenciales válidas, emite el evento de cierre del modal
        emit("closeModal", "logged");
    } else {
        // Credenciales inválidas, mostrar mensaje de error (opcional)
        alert("Nombre de usuario o contraseña incorrectos");
    }
}
const handleCancel = () => {
    emit("closeModal");
}
</script>

<style lang="postcss">
.panel {
    position: absolute;
    z-index: 99999;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    top: 120px;
    left: 350px;
    background-color: #ffffff;
    border-radius: 999px;
    width: 500px;
    height: 500px;
    padding: 30px;
    border: 1px solid white;

    h1 {
        color: rgb(0, 0, 0);
        width: 320px;
        font-size: 35px;
    }

    p {
        color: rgb(0, 0, 0);
        font-size: 14px;
    }

}

.input {
    color: rgb(255, 255, 255);
    width: 300px;
    height: 45px;
    border-radius: 16px;
    padding-left: 12px;
    background-color: black;
    font-size: 14px;

}

.boton-modal {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.middle-modal {
    display: flex;
    flex-direction: column;
    padding-top: 10px;
    padding-bottom: 30px;
    gap: 15px;
    width: 300px;
}

.olvido {
    text-align: end;
    padding-top: 7px;
}

.aux{
    background-color: white;
    position: absolute;
    z-index: 99999;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 999px;
    height: 150px;
    width: 150px;
    top: 120px;
    left: 900px;

    p {
        color: rgb(0, 0, 0);
        font-size: 14px;
    }

b {
        color: rgb(0, 0, 0);
        font-size: 14px;
}

b:hover {
        color: rgb(13, 0, 255);
        font-size: 14px;
        cursor: pointer;
}
}



</style>