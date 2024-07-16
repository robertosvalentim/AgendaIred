<template>
  <div class="edit-contact-container">
    <div class="edit-contact-box">
      <h2 class="edit-contact-title">Editar Contato</h2>
      <form @submit.prevent="saveContact" class="edit-contact-form">
        <div class="form-group">
          <label for="name" class="form-label">Nome:</label>
          <input
            type="text"
            id="name"
            v-model="currentContact.name"
            class="form-input"
            placeholder="Digite seu nome"
          />
        </div>
        <div class="form-group">
          <label for="address" class="form-label">Endereço:</label>
          <input
            type="text"
            id="address"
            v-model="currentContact.address"
            class="form-input"
            placeholder="Digite seu endereço"
          />
        </div>
        <div class="form-group">
          <label for="city" class="form-label">Cidade:</label>
          <input
            type="text"
            id="city"
            v-model="currentContact.city"
            class="form-input"
            placeholder="Digite sua cidade"
          />
        </div>
        <div class="form-group">
          <label for="phone" class="form-label">Telefone:</label>
          <input
            type="text"
            id="phone"
            v-model="currentContact.phone"
            class="form-input"
            placeholder="Digite seu telefone"
          />
        </div>
        <div class="form-group">
          <label for="email" class="form-label">Email:</label>
          <input
            type="text"
            id="email"
            v-model="currentContact.email"
            class="form-input"
            placeholder="Digite seu email"
          />
        </div>
        <div class="form-actions">
          <button type="button" class="button button-cancel" @click="$emit('cancel')">Descartar</button>
          <button type="submit" class="button button-save">Salvar</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'EditContact',
  props: {
    currentContact: {
      type: Object,
      required: true,
    },
  },
  methods: {
    saveContact() {
      this.$emit('save-contact', this.currentContact);
    },
  },
});
</script>

<style scoped>
.edit-contact-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.edit-contact-box {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  width: 300px;
}

.edit-contact-title {
  text-align: center;
  margin-bottom: 20px;
}

.edit-contact-form {
  display: flex;
  flex-direction: column;
}

.form-group {
  margin-bottom: 15px;
}

.form-label {
  margin-bottom: 5px;
}

.form-input {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.form-actions {
  display: flex;
  justify-content: space-between;
}

.button {
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.button-cancel {
  background-color: #f44336;
  color: white;
}

.button-save {
  background-color: #4caf50;
  color: white;
}
</style>


