<template>
  <div id="app">
    <h1>Meu Aplicativo de Contatos</h1>
    <!-- Lista de contatos -->
    <ContactList :contacts="contacts" @edit="editContact" @delete="deleteContact" />
    
    <!-- Formulário de edição de contato -->
    <EditContact v-if="editingContactIndex !== -1" :currentContact="contacts[editingContactIndex]" @save-contact="saveContact" @cancel="cancelEdit" />

    <!-- Formulário de adição de contato -->
    <AddContact v-if="showAddForm" @add="addContact" @cancel="cancelAdd" />
    
    <!-- Botão para mostrar o formulário de adição -->
    <button v-if="!showAddForm" @click="showAddForm = true">Adicionar Contato</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

interface Contact {
  id?: number;
  name: string;
  address: string;
  city: string;
  phone: string;
  email: string;
}

import ContactList from './components/ContactList.vue';
import EditContact from './components/EditContact.vue';
import AddContact from './components/AddContact.vue';

export default defineComponent({
  name: 'App',
  components: {
    ContactList,
    EditContact,
    AddContact,
  },
  data() {
    return {
      contacts: [
        { id: 1, name: 'John Doe', address: '123 Main St', city: 'Anytown', phone: '555-1234', email: 'john@example.com' },
        { id: 2, name: 'Jane Smith', address: '456 Oak Rd', city: 'Somewhere', phone: '555-5678', email: 'jane@example.com' },
        { id: 3, name: 'Bob Johnson', address: '789 Elm Ave', city: 'Elsewhere', phone: '555-9012', email: 'bob@example.com' }
      ] as Contact[],
      editingContactIndex: -1,
      showAddForm: false,
    };
  },
  methods: {
    editContact(index: number) {
      this.editingContactIndex = index;
    },
    deleteContact(index: number) {
      this.contacts.splice(index, 1);
    },
    saveContact(contact: Contact) {
      if (this.editingContactIndex !== -1) {
        this.contacts[this.editingContactIndex] = contact;
        this.editingContactIndex = -1;
      }
    },
    cancelEdit() {
      this.editingContactIndex = -1;
    },
    addContact(newContact: Contact) {
      // Simula a criação de um novo ID (substituir por lógica real se necessário)
      const newId = this.contacts.length > 0 ? this.contacts[this.contacts.length - 1].id! + 1 : 1;
      newContact.id = newId;
      
      // Adiciona o novo contato à lista
      this.contacts.push(newContact);
      
      // Oculta o formulário de adição após adicionar o contato
      this.showAddForm = false;
    },
    cancelAdd() {
      // Oculta o formulário de adição sem adicionar nenhum contato
      this.showAddForm = false;
    }
  }
});
</script>

<style>
#app {
  padding: 20px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

button {
  margin-bottom: 10px;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>

