<template>
    <q-page padding>
        <h4>Agregar Productos:</h4>

        <q-form 
            class="row q-col-gutter-md"
            @submit.prevent="procesarFormu"
            @reset="reset"
            ref="myForm"
        >

            <div class="col-12 col-sm-6">
                <q-input
                    label="Producto"
                    v-model="producto"
                    lazy-rules
                    :rules="[ val => val && val.length > 0 || 'Por favor escribe algo']"
                />
            
            </div>

            <div class="col-12 col-sm-6">
                <q-select 
                    label="Prioridad"
                    v-model="seleccion"
                    :options="opciones"
                    lazy-rules
                    :rules="[ val => val && val.length > 0 || 'Por favor selecciona']"
                 />
            
            </div>

            <div class="col-12">
                <q-toggle 
                    label="Aceptar los terminos"
                    v-model="terminos"
                />
            </div>


            <div class="col-12">
                    <q-btn
                    label="Agregar"
                    color="positive"
                    type="submit"
                />

                <q-btn
                    label="Eliminar"
                    color="negative"
                    outline
                    class="q-ml-sm"
                    :ripple="false"
                    type="reset"
                />
            
            </div>
        
        </q-form>

        <datos :productos="productos" />
        
    </q-page>
</template>

<script>
import {ref} from 'vue'
import { useQuasar } from 'quasar'
import Datos from 'src/components/Datos.vue'
export default {
  components: { Datos },
    setup() {
        const $q = useQuasar()
        const myForm = ref(null)
        const producto = ref(null)
        const seleccion = ref(null)
        const terminos = ref(false)
        const opciones = ['máxima', 'moderada', 'mínima'] 
        
        const productos = ref([])

        const procesarFormu = () => {
            console.log('me diste click al formulario')
            if(terminos.value === false){
                $q.notify({
                    color: 'red-5',
                    textColor: 'white',
                    icon: 'warning',
                    message: 'Tienes que Aceptar los Terminos'
                })
            }else {
                $q.notify({
                    color: 'green-4',
                    textColor: 'white',
                    icon: 'cloud_done',
                    message: 'Producto Agregado'
                })
                myForm.value.resetValidation()

                //Procesar el formulario
                productos.value = [...productos.value, {
                    producto: producto.value,
                    prioridad: seleccion.value
                }]
                
                reset()
            }
        }

        const reset = () => {
            producto.value = null
            seleccion.value = null
            terminos.value = false
        }

        return {
            producto,
            seleccion,
            opciones,
            procesarFormu,
            terminos,
            reset,
            myForm,
            productos
        }
    },
}
</script>