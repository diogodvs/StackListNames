<template>
  <HeaderComponent></HeaderComponent>
  <div class="h-screen bg-dark-700">
    <div class="max-w-[90rem] my-0 mx-auto px-24 py-20">
      <h1 class="font-semibold text-3xl text-gray-200">
        Lista dos Alunos do Curso
      </h1>
      <div class="flex justify-between items-center mt-10">

        <div class="flex flex-col w-[48%]">
          <label class="font-semibold text-base text-gray-300">
            Pesquisar
          </label>
          <input type="text" placeholder="Nome do Aluno"
            class="bg-dark-400 rounded-lg mt-2 border-none py-3 px-5 text-white-600 text-base" />
        </div>

        <div class="flex flex-col w-[48%]">
          <label class="font-semibold text-base text-gray-300">
            Nacionalidade
          </label>

          <select name="nacionalidade" id="nacionalidade"
            class="bg-dark-400 rounded-lg mt-2 border-none py-3 px-5 text-white-600 text-base hover:cursor-pointer">
            <option value="">Todas</option>
          </select>
        </div>
      </div>

      <div class="overflow-x-auto relative shadow-md sm:rounded-lg mt-8">
        <table class="w-full text-base text-left text-gray-400 bg-dark-400">
          <thead class="">
            <tr>
              <th scope="col" class="py-3 px-6">Nome</th>
              <th scope="col" class="py-3 px-6">Sexo</th>
              <th scope="col" class="py-3 px-6">Nacionalidade</th>
              <th scope="col" class="py-3 px-6">Ação</th>
            </tr>
          </thead>
          <tbody>
            <tr class="border-t border-grey-200">
              <th scope="row" class="py-4 px-6 font-medium text-white-400 " >Diogo Silva</th>
              <th scope="row" class="py-4 px-6 font-medium text-white-400 ">Masculino</th>
              <th scope="row" class="py-4 px-6 font-medium text-white-400 ">Brasileiro</th>
              <th scope="row" class="py-4 px-6 font-medium text-white-400 "> 
                <button class="bg-dark-500 rounded py-0.5 px-1.5">Visualizar</button>
              </th>
            </tr>
          </tbody>
        </table>
      </div>

    </div>
  </div>
</template>

<script>
import HeaderComponent from '@/components/HeaderComponent.vue'
export default {
  name: 'App',
  components: {
    HeaderComponent
  }
}
</script>

<style>
#app {}
</style>
