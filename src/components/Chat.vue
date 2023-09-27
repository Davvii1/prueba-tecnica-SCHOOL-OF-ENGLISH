<template>
  <div id="chat-container">
    <div class="chat-header">
      <div class="contact-info">
        <img
          class="UserProfilePic"
          src="https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png"
          alt="UserProfilePic"
        />
        <div>
          <p>{{ contact.name }}</p>
          <p>{{ contact.description }}</p>
        </div>
      </div>
      <UserActions />
    </div>
    <div id="chat-messages">
      <div id="messages-container" v-for="message in messages" :key="message.id">
        <p v-if="message.incoming" class="incoming-message">
          {{ message.content }}
        </p>
        <p v-else class="outgoing-message">
          {{ message.content }}
        </p>
      </div>
    </div>
    <div id="chat-new-message">
      <input
        id="newMessageInput"
        type="text"
        placeholder="Escribe un mensaje..."
        v-model="newMessage"
      />
      <div id="fileLabel">
        <label for="attachFile">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            fill="currentColor"
            class="bi bi-paperclip"
            viewBox="0 0 16 16"
          >
            <path
              d="M4.5 3a2.5 2.5 0 0 1 5 0v9a1.5 1.5 0 0 1-3 0V5a.5.5 0 0 1 1 0v7a.5.5 0 0 0 1 0V3a1.5 1.5 0 1 0-3 0v9a2.5 2.5 0 0 0 5 0V5a.5.5 0 0 1 1 0v7a3.5 3.5 0 1 1-7 0V3z"
            />
          </svg>
        </label>
        <input type="file" id="attachFile" />
      </div>
      <button id="submitBtn" @click="sendMessage">Send</button>
    </div>
  </div>
</template>

<script>
import UserActions from './UserActions.vue'
export default {
  data() {
    return {
      contact: {
        name: 'Contacto 1',
        picture: 'https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png',
        description: 'Descripción del contacto'
      },
      messages: [
        { id: 1, incoming: true, content: 'Hola como estas', date: new Date().getHours() },
        { id: 2, incoming: false, content: 'Bien y tu', date: new Date().getHours(), read: true }
      ],
      newMessage: ''
    }
  },
  components: {
    UserActions
  },
  methods: {
    sendMessage() {
      this.messages.push({
        id: Math.floor(Math.random() * 100),
        from_user_id: 2,
        content: this.newMessage,
        date: new Date().getHours(),
        read: false
      })
      this.message = '';
    }
  }
}
</script>

<style scoped>
.UserProfilePic {
  height: 2.5rem;
  border-radius: 20px;
  margin-right: 0.5rem;
}

.contact-info {
  display: flex;
  flex-direction: row;
}

.chat-header {
  width: auto;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid rgba(128, 128, 128, 0.5);
  height: 3.5rem;
  padding-left: 1rem;
}

#chat-container {
  width: 70%;
  height: 95%;
  /* border: 1px solid red; */
  display: flex;
  flex-direction: column;
  margin: 1rem;
}

button {
  border-radius: 5px;
  background-color: #965afb;
  color: white;
  border: 0px;
  padding-top: 0.25rem;
  padding-bottom: 0.25rem;
  padding-left: 0.75rem;
  padding-right: 0.75rem;
}

#chat-messages {
  padding: 1rem;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

#messages-container {
  display: flex;
  flex-direction: column;
}

.outgoing-message {
  background-color: #965afb;
  width: max-content;
  color: white;
  border-radius: 15px;
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
  padding-left: 1rem;
  padding-right: 1rem;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.26);
  align-self: flex-end;
  margin-bottom: 0.5rem;
}

.incoming-message {
  background-color: white;
  width: max-content;
  border-radius: 15px;
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
  padding-left: 1rem;
  padding-right: 1rem;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.26);
  margin-bottom: 0.5rem;
}

#chat-new-message {
  width: auto;
  display: flex;
  align-items: center;
  padding-left: 2rem;
  padding-right: 2rem;
}

#fileLabel {
  height: 3rem;
  width: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

#submitBtn {
  height: 3rem;
  width: 5rem;
}

#attachFile {
  display: none;
}

#newMessageInput {
  background-color: white;
  width: max-content;
  border-radius: 5x;
  border-width: 1px;
  border-color: rgba(128, 128, 128, 0.2);
  margin-bottom: 2rem;
  margin-top: 2rem;
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
  padding-left: 1rem;
  padding-right: 1rem;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.26);
  flex-grow: 1;
}
</style>