<template>
  <div id="app">
    
    <div class="jumbotron jumbotron-fluid">
      <div class="container">
        <h1 class="display-4">Formulários no Vue</h1>
        <p class="lead">Treinando a manipulação de formulários</p>
      </div>
    </div>

    <div class="container">

      <div class="row">

        <!-- formulario -->
        <div class="col-sm-6">

          <h3>Preencha abaixo</h3>

          <form>

            <div class="form-group">
              <label>Nome:</label>
              <input 
              v-model.lazy.trim="desenvolvedor.nome"
              type="text" 
              class="form-control" 
              placeholder="Seu nome">
            </div>

            <div class="form-group">
              <label>Endereço de email:</label>
              <input 
              v-model.lazy.trim="desenvolvedor.email"
              type="email" 
              class="form-control" 
              placeholder="Seu email">
            </div>

            <div class="form-group">
              <label>Idade:</label>
              <input 
              v-model.lazy.trim="desenvolvedor.idade"
              type="number"
              class="form-control" 
              placeholder="Sua idade">
            </div>

            <div class="form-group">

              <p>Gênero:</p>

              <div class="form-check form-check-inline">
                <input 
                
                type="radio" 
                class="form-check-input" 
                value="Masculino"
                v-model="desenvolvedor.genero">
                <label class="form-check-label">Masculino</label>
              </div>

              <div class="form-check form-check-inline">
                <input 
                type="radio" 
                class="form-check-input" 
                value="Feminino"
                v-model="desenvolvedor.genero">
                <label class="form-check-label">Feminino</label>
              </div>

            </div>

            <div class="form-group">
              <label>Ocupação:</label>
              <select 
              v-model="desenvolvedor.ocupacao"
              class="form-control" 
              placeholder="Seu email">
              <option value="" disabled>Selecione uma opção...</option>
                <option 
                v-for="(ocupacao, indice) in ocupacoes"
                :key="indice"
                :value="ocupacao"
                :selected="ocupacao === 'Desenvolvedor Back End'">
                {{ ocupacao }}
                </option>
              </select>
            </div>  

            <div class="form-group">

              <p>Tecnologias:</p>

              <div class="form-check form-check-inline">
                <input 
                v-model="desenvolvedor.tecnologias"
                type="checkbox" 
                class="form-check-input"
                value="JavaScript">
                <label class="form-check-label">JavaScript</label>
              </div>

              <div class="form-check form-check-inline">
                <input 
                v-model="desenvolvedor.tecnologias"
                type="checkbox" 
                class="form-check-input"
                value="Vue JS">
                <label class="form-check-label">Vue JS</label>
              </div>

              <div class="form-check form-check-inline">
                <input 
                v-model="desenvolvedor.tecnologias"
                type="checkbox" 
                class="form-check-input" 
                value="Vuex">
                <label class="form-check-label">Vuex</label>
              </div>

              <div class="form-check form-check-inline">
                <input 
                v-model="desenvolvedor.tecnologias"
                type="checkbox" 
                class="form-check-input" 
                value="Vue Router">
                <label class="form-check-label">Vue Router</label>
              </div>

            </div>      

            <div class="form-group">
              <label>Resumo de perfil:</label>
              <textarea 
              v-model="desenvolvedor.biografia"
              class="form-control" 
              placeholder="Conte-nos um pouco sobre você...">
              </textarea>
            </div>

            <div class="form-group">

              <div class="form-check form-check-inline">
                <input 
                v-model="desenvolvedor.notificacoes"
                type="checkbox"
                class="form-check-input"
                true-value="Sim"
                false-value="Não">
                <label class="form-check-label">Receber notificações por email</label>
              </div>

            </div>

            <button class="btn btn-secondary" type="reset">Resetar</button>
            <button class="btn btn-success" type="button" @click="enviar">Enviar</button>

          </form>

        </div>

        <!-- saida -->
        <div class="col-sm-6">

          <h3>Saída</h3>

          <div class="card">

            <div class="card-header">Dados</div>

            <ul class="list-group list-group-flush">
              <li class="list-group-item"><strong>Nome: {{ desenvolvedor.nome }}</strong></li>
              <li class="list-group-item"><strong>Email: {{ desenvolvedor.email }}</strong> </li>
              <li class="list-group-item"><strong>Idade: {{ desenvolvedor.idade }}</strong></li>
              <li class="list-group-item"><strong>Gênero: {{ desenvolvedor.genero }}</strong> </li>
              <li class="list-group-item"><strong>Ocupação: {{ desenvolvedor.ocupacao }}</strong> </li>
              <li class="list-group-item">
                <strong>Tecnologias: </strong> 
                <ul>
                  <li
                  v-for="(tecnologia, indice) in desenvolvedor.tecnologias"
                  :key="indice">
                    {{ tecnologia }}
                  </li>
                </ul>
                </li>
              <li class="list-group-item"> 
                <strong>Biografia: <pre>{{ desenvolvedor.biografia }}</pre></strong> </li>
              <li class="list-group-item"><strong>Receber notificações? {{ desenvolvedor.notificacoes }}</strong> </li>
            </ul>

            <div class="card-header">Model</div>

            <div class="card-body">
              <pre><code>{{ { desenvolvedor } }}</code></pre>
            </div>

          </div>

        </div>

      </div>

    </div>

  </div>
</template>
<script>
export default {
  data() {
    return {
     desenvolvedor: {
       nome: 'Wladimir',
       email: '',
       idade: 28,
       biografia: 'Sou desenvolvedor desde 2010',
       genero: 'masculino',
       notificacoes: 'Não',
       tecnologias: [],
       ocupacao: ''
     },
     ocupacoes: [
       'Desenvolvedor Front end Web',
       'Desenvolvedor Back End',
       'Desenvolvedor Front End Mobile',
       'Desenvolvedor Front End Web e Mobile',
       'Desenvolvedor Full Stack' 
     ]
    }
  },
  methods: {
    enviar(event) {
       const formularioEnviado = Object.assign({}, this.desenvolvedor)
       console.log('Formulário enviado!', formularioEnviado)
    }
  }
}
</script>

<style scoped>
  .btn {
    margin-right: 5px;
  }
</style>