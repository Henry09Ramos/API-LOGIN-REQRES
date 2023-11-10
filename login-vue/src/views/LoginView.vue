

<template>
    <div class="min-h-screen flex items-center justify-center bg-gray-100">
       <div class="bg-white p-8 shadow-md rounded-md w-96">
         <h2 class="text-2xl font-semibold mb-4">Inicio de Sesión</h2>
         <form @submit.prevent="login">
           
           <div class="mb-4">
             <label for="email" class="block text-sm font-medium text-gray-700">Correo Electrónico</label>
             <input v-model="email" type="email" id="email" name="email" required class="w-full px-3 py-2 mt-1 bg-gray-100 border rounded-md focus:ring focus:ring-gray-300">
           </div>
           <div class="mb-4">
             <label for="password" class="block text-sm font-medium text-gray-700">Contraseña</label>
             <input v-model="password" type="password" id="password" name="password" required class="w-full px-3 py-2 mt-1 bg-gray-100 border rounded-md focus:ring focus:ring-gray-300">
            </div>
           <div>
           </div>
             <button type="submit" class="w-full py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700 focus:ring focus:ring-blue-300" >Iniciar Sesión</button>
          
         </form>
       </div>
     </div>
     <div id="example-2">
  <!-- `saludar` es el nombre de un método definido a continuación -->
</div>
 </template>
 
 <script lang="ts" setup>
 
 
 
   import { ref } from 'vue';
   import axios from 'axios';
    import  router  from '../routes';
   import  {useAuthStore} from '../components/auth' 

   const authStore = useAuthStore();
   const email = ref('');
   const password = ref('');

 
   const login = async () => {
     try {
       const response = await axios.post('https://reqres.in/api/login', {
         email: email.value,
         password: password.value,
         

       });
       
       console.log('Inicio de sesión exitoso', response.data);
  authStore.setAuthenticated(true);
        router.push('/home');
        alert("inicio de sesion exitoso")
        
     } catch (error) {
       console.error('Error al iniciar sesión', error);
        alert("Error Al iniciar sesion")
        
     }
   };

  
 
   
 </script>
 
 
 
 