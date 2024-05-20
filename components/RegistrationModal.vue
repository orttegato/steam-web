<template v-show="registrationModalActive">
    <div class="panel-registro">
        <h1>Registrarse</h1>
        <div class="middle-modal">
            <div>
                <label for="newName">
                    <p>Nombre de usuario:</p>
                </label>
                <input class="input" type="text" v-model="newFormData.name" id="newName"
                    placeholder="Introduce tu nuevo nombre de usuario" />
            </div>
            <div>
                <label for="newPassword">
                    <p>Contraseña:</p>
                </label>
                <input class="input" type="password" v-model="newFormData.password" id="newPassword"
                    placeholder="Introduce tu nueva contraseña" />
            </div>
        </div>
        <div class="boton-modal">
            <BaseButton type="submit" @click="submitRegistration">Registrarse</BaseButton>
            <button @click.prevent="closeRegistrationModal">
                <p>Cancelar</p>
            </button>
        </div>
    </div>

    <div class="aux-registro" v-show="!registrationModalActive">
        <p>¿Ya tienes cuenta?</p>
        <p><b @click="openIniciarModal">Inicia sesión</b></p>
    </div>

    <IniciarModal v-if="iniciarmodalActive" @close-modal="closeIniciarModal" />
</template>

<script setup>
import { ref } from 'vue'
const emit = defineEmits(['closeModal', 'openRegistrationModal', 'openIniciarModal'])

// Estado para los datos del formulario de registro
const newFormData = ref({
    name: '',
    password: ''
})

const iniciarmodalActive = ref(false);
const registrationModalActive = ref(false);

const openIniciarModal = () => {
    iniciarmodalActive.value = true;
    registrationModalActive.value = false;
    emit("closeModal");

};

const closeIniciarModal = (e) => {
    iniciarmodalActive.value = false;
    registrationModalActive.value = true;
}




// Estado para controlar la visibilidad del modal de registro

// Método para enviar el formulario de registro
const submitRegistration = async () => {
    // Aquí puedes implementar la lógica de registro
    // Por ejemplo, enviar una solicitud al servidor
    // para crear una nueva cuenta con newFormData

    // Una vez que se completa el registro exitosamente:
    // Cierra el modal de registro
    registrationModalActive.value = false
    // Emite un evento para indicar que el usuario ha iniciado sesión (puede ser necesario en tu implementación)
    emit("closeModal", "logged")
}

</script>


<style lang="postcss">
.panel-registro {
    position: absolute;
    z-index: 99999;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    top: 120px;
    left: 650px;
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


.aux-registro{
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
    top: 420px;
    left: 450px;

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