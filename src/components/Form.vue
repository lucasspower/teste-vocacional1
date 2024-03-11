<template>
  <div class="container">
    <li v-for="(resultado, index) in formulario.questoes" :key="index">
      {{ resultado.questao }} --{{ resultado.resultado }}
    </li>
    <fieldset v-for="(pergunta, index) in formulario.questoes" :key="index">
      <h3>{{ pergunta.pergunta }} -- Questão: {{ pergunta.questao }}</h3>
      <div
        class="form-check"
        v-for="(alternativa, indexe) in pergunta.alternativas"
        :key="indexe"
      >
        <label
          class="form-check-label"
          :for="pergunta.questao + indexe"
          :name="pergunta.pergunta"
        >
          <input
            v-model="pergunta.resultado"
            :value="indexe"
            class="form-check-input"
            type="radio"
            :name="pergunta.pergunta"
            :id="pergunta.questao + indexe"
          />
          <span class=""> {{ indexe }} - </span>
          {{ alternativa }}
        </label>
      </div>
      <FooterForm />
    </fieldset>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";
import FooterForm from "./FooterForm.vue";
const formulario = reactive({
  questoes: [
    {
      questao: 1,
      pergunta: "Materia",
      alternativas: {
        a: "História, Português e Geografia.",
        b: "Química",
        c: "Matemática",
        d: "Biologia",
      },
      resultado: "",
    },
    {
      questao: 2,
      pergunta: "Idade",
      alternativas: {
        a: "10",
        b: "112",
        c: "15",
        d: "100",
      },
    },
    {
      questao: 3,
      pergunta: "sexo",
      alternativas: {
        a: "mas",
        b: "fem",
        c: "Feminino",
        d: "Masculino",
      },
    },
  ],
});
</script>
