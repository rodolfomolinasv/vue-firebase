<template>
    <div>
        <h2>Tareas por hacer</h2>
        <ul>
            <li v-for="tarea in tareasPendientes" :key="tarea.nombre">
                <a href="#" @click="actualizarTarea(tarea)" v-text="tarea.nombre"></a>
            </li>
        </ul>
        <h2>Tareas finalizadas</h2>
        <li v-for="tarea in tareasFinalizadas" :key="tarea.nombre">
            <a href="#" @click="actualizarTarea(tarea)" v-text="tarea.nombre"></a>
        </li>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tareas: [
                {nombre: 'Aprender Vue.js', completado: false},
                {nombre: 'Grabar el módulo de Vuex', completado: false},
                {nombre: 'Responder comentarios', completado: false},
                {nombre: 'Salir a correr para despejarme', completado: false},
                {nombre: 'Diseñar el módulo de Firebase', completado: false},
                {nombre: 'Diseñar el ejercicio final', completado: false},
            ],
            finalizadas: []
        }
    },
    methods: {
        actualizarTarea(tarea){
            tarea.completado = !tarea.completado;
        }
    },
    computed: {
        tareasPendientes(){
            return this.tareas.filter(tarea => !tarea.completado);
        },
        tareasFinalizadas(){
            return this.tareas.filter(tarea => tarea.completado);
        }
    }
}
</script>
<style scoped>
    li a {
        color: red;
    }
</style>
