<script setup>
import { ref, watch } from "vue";

const packageData = ref({
  name: "",
  version: "",
  description: ""
});

const formattedPackageJson = ref(
  JSON.stringify(packageData.value, null, 2)
);

watch(packageData, () => {
  formattedPackageJson.value = JSON.stringify(packageData.value, null, 2);
}, {
  deep: true
});

const newKeyword = ref("");

const addKeyword = () => {
  if (newKeyword.value.trim() !== "") {
    if (!packageData.value.keywords) {
      packageData.value.keywords = [];
    }
    packageData.value.keywords.push(newKeyword.value.trim());
    newKeyword.value = "";
  }
};

const removeKeyword = (index) => {
  packageData.value.keywords.splice(index, 1);
  if (packageData.value.keywords.length === 0) {
    delete packageData.value.keywords;
  }
};

const dependencies = ref([]);

const addDependency = () => {
  dependencies.value.push({ name: "", version: "" });
};

const updateDependency = (index, key, value) => {
  dependencies.value[index][key] = value;

  packageData.value.dependencies = dependencies.value.reduce((acc, dep) => {
    if (dep.name.trim() && dep.version.trim()) {
      acc[dep.name] = dep.version;
    }
    return acc;
  }, {});
};

const removeDependency = (index) => {
  dependencies.value.splice(index, 1);

  packageData.value.dependencies = dependencies.value.reduce((acc, dep) => {
    if (dep.name.trim() && dep.version.trim()) {
      acc[dep.name] = dep.version;
    }
    return acc;
  }, {});
};
</script>

<template>
  <div class="app">
    <h1>Créateur de fichier `package.json`</h1>

    <form @submit.prevent>
      <label for="name">Nom du package :</label>
      <input type="text" id="name" v-model="packageData.name" placeholder="vue-app" required />

      <label for="version">Version :</label>
      <input type="text" id="version" v-model="packageData.version" placeholder="1.0.0" required />

      <label for="description">Description :</label>
      <textarea id="description" v-model="packageData.description" placeholder="Description du package"></textarea>

      <h2>Mots-clés :</h2>
      <div>
        <input type="text" v-model="newKeyword" placeholder="Ajouter un mot-clé" />
        <button @click="addKeyword" type="button">Ajouter</button>
      </div>
      <ul>
        <li v-for="(keyword, index) in packageData.keywords" :key="index">
          {{ keyword }}
          <button @click="removeKeyword(index)" type="button">Supprimer</button>
        </li>
      </ul>

      <h2>Dépendances :</h2>
      <button @click="addDependency" type="button">Ajouter une dépendance</button>
      <div v-for="(dependency, index) in dependencies" :key="index">
        <label>Nom du package :</label>
        <input type="text" v-model="dependency.name" @input="updateDependency(index, 'name', dependency.name)"
          placeholder="react" />

        <label>Version du package :</label>
        <input type="text" v-model="dependency.version" @input="updateDependency(index, 'version', dependency.version)"
          placeholder="1.0.0" />

        <button @click="removeDependency(index)" type="button">Supprimer</button>
      </div>
    </form>

    <h2>Prévisualisation du `package.json` :</h2>
    <pre><code>{{ formattedPackageJson }}</code></pre>
  </div>
</template>
