<template>
  <HeaderComponent></HeaderComponent>
  <div class="h-full bg-dark-700 min-h-screen">
    <div class="max-w-[90rem] my-0 mx-auto px-24 py-20">
      <h1 class="font-semibold text-3xl text-gray-200">
        Lista dos Alunos do Curso
      </h1>
      <div class="flex justify-between items-center mt-10">

        <div class="flex flex-col w-[48%]">
          <label class="font-semibold text-base text-gray-300">
            Pesquisar
          </label>
          <input 
            type="text" 
            placeholder="Nome do Aluno"
            class="bg-dark-400 rounded-lg mt-2 border-none py-3 px-5 text-white-600 text-base" 
            @keyup="onSearch"
            v-model="search"
          />
        </div>

        <div class="flex flex-col w-[48%]">
          <label class="font-semibold text-base text-gray-300">
            Nacionalidade
          </label>

          <select 
            name="nacionalidade" 
            id="nacionalidade"
            class="bg-dark-400 rounded-lg mt-2 border-none py-3 px-5 text-white-600 text-base hover:cursor-pointer"
            @change="onSearch"
            v-model="searchCountry"
            >
            <option value="">Todas</option>
            <option
              v-for="nat in $store.state.dataUser"
              :key="nat.location.country.pastcode"
            >{{nat.location.country}}</option>
          </select>
        </div>
      </div>

      <div class="overflow-x-auto relative shadow-md sm:rounded-lg mt-8">
        <table class="w-full text-base text-left text-gray-400 bg-dark-400">
          <thead class="">
            <tr >
              <th scope="col" class="py-3 px-6">Nome</th>
              <th scope="col" class="py-3 px-6">Sexo</th>
              <th scope="col" class="py-3 px-6">Nacionalidade</th>
              <th scope="col" class="py-3 px-6">Ação</th>
            </tr>
          </thead>
          <tbody>
            <tr 
            class="border-t border-grey-200" 
            v-for="user in onSearch()"
            :key="user.id.value"
            >
            <th scope="row" class="py-4 px-6 font-medium text-white-400 " >
              {{`${user.name.first} ${user.name.last}`}}
            </th>
              <th scope="row" class="py-4 px-6 font-medium text-white-400 ">
                {{user.gender}}
              </th>
              <th scope="row" class="py-4 px-6 font-medium text-white-400 ">
                {{user.location.country}}
              </th>
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
  },
  data(){
    return{
      loading: false,
      search: '',
      searchCountry: ''
    }
  },
  created(){
    this.loading = true;
    this.$store.dispatch('getUsers').finally(() => {this.loading = false})
  },
  methods: {
    onSearch(){
      if(this.search.length > 0){
        return this.$store.state.dataUser.filter(a => 
        (a.name.first.toUpperCase()).includes(this.search.toUpperCase()))

      } else if(this.searchCountry.length > 0){
        this.$store.state.dataUser.filter(a => 
        (a.location.country.toUpperCase()).includes(this.searchCountry.toUpperCase()))

      } else {
        return this.$store.state.dataUser;
      }
    }
  }


}
</script>

<style>
#app {}
</style>
