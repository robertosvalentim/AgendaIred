<template>
  <div class="contact-list-container">
    <h2 class="contact-list-title">Lista de Contatos</h2>
    <div class="contact-list">
      <div class="contact-item" v-for="(contact, index) in contacts" :key="index">
        <div class="contact-info">
          <h3 class="contact-name">{{ contact.name }}</h3>
          <p class="contact-details">{{ contact.address }}, {{ contact.city }}</p>
          <p class="contact-details">{{ contact.phone }}</p>
          <p class="contact-details">{{ contact.email }}</p>
        </div>
        <div class="contact-actions">
          <button class="button button-edit" @click="$emit('edit', index)">
            Editar
          </button>
          <button class="button button-delete" @click="$emit('delete', index)">
            Excluir
          </button>
        </div>
      </div>
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
  name: 'ContactList',
  props: {
    contacts: {
      type: Array as () => Contact[],
      required: true,
    },
  },
});
</script>

<style scoped>
.contact-list-container {
  padding: 20px;
}

.contact-list-title {
  text-align: center;
  margin-bottom: 20px;
}

.contact-list {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.contact-item {
  background: white;
  padding: 15px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.contact-info {
  margin-bottom: 10px;
}

.contact-name {
  margin: 0;
  font-size: 1.2em;
}

.contact-details {
  margin: 0;
}

.contact-actions {
  display: flex;
  gap: 10px;
}

.button {
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.button-edit {
  background: #2196f3;
  color: white;
}

.button-delete {
  background: #f44336;
  color: white;
}
</style>

