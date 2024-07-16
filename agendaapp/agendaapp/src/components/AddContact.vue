AddContact.vue

<template>
  <div class="add-contact-container">
    <div class="add-contact-box">
      <h2 class="add-contact-title">Adicionar Novo Contato</h2>
      <form @submit.prevent="addContact" class="add-contact-form">
        <div class="form-group">
          <label for="name" class="form-label">Nome:</label>
          <input
            type="text"
            id="name"
            v-model="newContact.name"
            class="form-input"
            placeholder="Digite o nome do contato"
            required
          />
        </div>
        <div class="form-group">
          <label for="address" class="form-label">Endereço:</label>
          <input
            type="text"
            id="address"
            v-model="newContact.address"
            class="form-input"
            placeholder="Digite o endereço do contato"
          />
        </div>
        <div class="form-group">
          <label for="city" class="form-label">Cidade:</label>
          <input
            type="text"
            id="city"
            v-model="newContact.city"
            class="form-input"
            placeholder="Digite a cidade do contato"
          />
        </div>
        <div class="form-group">
          <label for="phone" class="form-label">Telefone:</label>
          <input
            type="text"
            id="phone"
            v-model="newContact.phone"
            class="form-input"
            placeholder="Digite o telefone do contato"
          />
        </div>
        <div class="form-group">
          <label for="email" class="form-label">Email:</label>
          <input
            type="email"
            id="email"
            v-model="newContact.email"
            class="form-input"
            placeholder="Digite o email do contato"
          />
        </div>
        <div class="form-actions">
          <button type="button" class="button button-cancel" @click="cancelAdd">
            Cancelar
          </button>
          <button type="submit" class="button button-add">Adicionar</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

interface Contact {
  name: string;
  address: string;
  city: string;
  phone: string;
  email: string;
}

export default defineComponent({
  name: 'AddContact',
  emits: ['add', 'cancel'],
  data() {
    return {
      newContact: {
        name: '',
        address: '',
        city: '',
        phone: '',
        email: ''
      } as Contact
    };
  },
  methods: {
    addContact() {
      // Emitir evento para adicionar novo contato
      this.$emit('add', this.newContact);

      // Limpar os campos do formulário
      this.newContact = {
        name: '',
        address: '',
        city: '',
        phone: '',
        email: ''
      };
    },
    cancelAdd() {
      // Emitir evento de cancelamento
      this.$emit('cancel');
    }
  }
});
</script>

<style scoped>
.add-contact-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.add-contact-box {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  width: 300px;
}

.add-contact-title {
  text-align: center;
  margin-bottom: 20px;
}

.add-contact-form {
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
  background: #f44336;
  color: white;
}

.button-add {
  background: #4caf50;
  color: white;
}
</style>


