<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_site: "",
      novo_editora: "",
      jogadores: [
        {
          id: "442e6fe2-e800-11ec-8fea-0242ac120002",
          acao: "Editora Rocco",
          site:"https://www.rocco.com.br/",
        },
        {
          id: "5116842e-e800-11ec-8fea-0242ac120002",
          acao: "Editora Record LTDA.",
           site:"https://www.record.com.br/categoria-produto/livros/",
        },
        {
          id: "5b745d2e-e800-11ec-8fea-0242ac120002",
          acao: "Lafonte",
           site:"https://www.editoralafonte.com.br/",
        },
        {
          id: "6043b8ae-e800-11ec-8fea-0242ac120002",
          acao: "Editora Record LTDA.",
          site:"https://www.record.com.br/categoria-produto/livros/",
        },
      ],
    };
  },
  methods: {
    salvar() {
      const id = uuid();
      this.jogadores.push({
        id: id,
        acao: this.novo_editora,
        site: this.novo_site
      });
    },

    excluir(jogador) {
      const indice = this.jogadores.indexOf(jogador);
      this.jogadores.splice(indice, 1);
    },
    alerta() {
      alert("ok");
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Editoras</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Nome" v-model="novo_editora" />
       <input type="text" placeholder="Nome" v-model="novo_site" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-jogadores">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Editora</th>
             <th>Site</th>
            <th>Ação</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in jogadores" :key="livro.id">
            <td>{{ livro.id }}</td>
            <td>{{ livro.acao }}</td>
            <td>{{ livro.site}}</td>
            <td>
              <button @click="alerta">Editar</button>
              <button @click="excluir">excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped></style>
