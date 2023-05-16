<script setup>
 import {ref} from 'vue';
  const courses= ref([
    {
      id:1,
      name:'Curso de Vue',
      url:'https://as.com'
  },
  {
      id:2,
      name:'Curso de Ilustrastor',
      url:'https://marca.com'
  }
  ])

  let newCourse = {}

  const saveInfoCourse= (event, field)=>{
    const value = event.target.value;
    newCourse[field] = value;
  }

  const saveNewCourse = ()=>{
    courses.value.push({
      ...newCourse,
      id:courses.value[courses.value.length - 1].id + 1
    })
  }
  
  </script>

<template>
  <header class="p-6 border-b-2">
    <a href="#" class="mr-4">Cursos</a>
    <a href="#">Nuevo Curso</a>
  </header>

  <main class="mt-4">
   <section>
    <h3>Añade un nuevo Curso</h3>
    <form class="flex mb-4">
      <input type="text" placeholder="Bombre Curso" class="input input-bordered w-full max-w-xs mr-3" @input="saveInfoCourse($event, 'name')">
      <input type="text" placeholder="Url Curso" class="input input-bordered w-full max-w-xs mr-4" @input="saveInfoCourse($event, 'url')">
      <button type="button" class="btn btn-success" @click="saveNewCourse">Crear</button>
    </form>
   </section>
    <div class="overflow-x-auto">
      <table class="table w-full">
        <!-- head -->
          <thead>
            <tr>
              <th></th>
              <th>Nombre</th>
              <th>url</th>
            </tr>
          </thead>
          <tbody>
            <!-- row 1 -->
            <tr v-for="course in courses" :key="course.id">
              <th>{{course.id}}</th>
              <td>{{course.name}}</td>
              <td>{{course.url}}</td>
            </tr>
          </tbody>
        </table>
    </div>

  </main>

</template>

