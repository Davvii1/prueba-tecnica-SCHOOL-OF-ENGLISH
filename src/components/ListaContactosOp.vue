<template>
  <div id="chats-container">
    <div id="search-container">
      <img
        class="UserProfilePic"
        src="https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png"
        alt="UserProfilePic"
      />
      <div id="searchBar">
        <input id="searchinput" type="text" placeholder="Buscar..." />
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="16"
          height="16"
          fill="currentColor"
          class="bi bi-search"
          viewBox="0 0 16 16"
          id="search-svg"
        >
          <path
            d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"
          />
        </svg>
      </div>
    </div>
    <h2>Chats</h2>
    <!-- Contacts messages -->
    <div v-for="message in messages" :key="message.id" class="messages">
      <div v-if="message.active" class="message-container">
        <img
          class="UserProfilePic"
          src="https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png"
          alt="UserProfilePic"
        />
        <div class="contact-data">
          <h4>{{ message.from }}</h4>
          <p>{{ message.content }}</p>
        </div>
      </div>
      <div v-else class="message-container-unactive">
        <img
          class="UserProfilePic"
          src="https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png"
          alt="UserProfilePic"
        />
        <div class="contact-data">
          <h4>{{ message.from }}</h4>
          <p>{{ message.content }}</p>
        </div>
      </div>
    </div>
    <h2>Contactos</h2>
    <div v-for="contact in contacts" :key="contact" class="contacts">
      <div class="contact-container">
        <img
          class="UserProfilePic"
          src="https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png"
          alt="UserProfilePic"
        />
        <div class="contact-data">
          <h4>{{ contact.name }}</h4>
          <p>{{ contact.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [
        {
          id: 1,
          from: 'Pedro Rodríguez',
          content: 'Hola como estas',
          active: true
        },
        {
          id: 2,
          from: 'David Garrido',
          content: 'Ya voy para la casa'
        }
      ],
      contacts: [
        {
          name: 'Contacto 1',
          picture: 'https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png',
          description: 'Descripción del contacto'
        },
        {
          name: 'Contacto 2',
          picture: 'https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png',
          description: 'Descripción del contacto'
        },
        {
          name: 'Contacto 3',
          picture: 'https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png',
          description: 'Descripción del contacto'
        },
        {
          name: 'Contacto 4',
          picture: 'https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png',
          description: 'Descripción del contacto'
        },
        {
          name: 'Contacto 5',
          picture: 'https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_1280.png',
          description: 'Descripción del contacto'
        }
      ],
      search: ''
    }
  }
}
</script>

<style scoped>
#searchBar {
  width: 100%;
  position: relative;
  display: flex;
  flex-direction: row;
  align-items: center;
}

#search-svg {
  position: absolute;
  left: 10px;
}

#chats-container {
  width: 30%;
  height: 95%;
  background-color: white;
  border-right: 1px solid gray;
}

h2 {
  color: #965afb;
}
.message-container-unactive {
  width: auto;
  /* border: 1px solid green; */
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 5px;
  background-color: white;
  padding-top: 1rem;
  padding-bottom: 1rem;
  padding-left: 0.5rem;
  padding-right: 0.5rem;
  border-radius: 10px;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.26);
}

.message-container {
  width: auto;
  color: white;
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 5px;
  background-color: #965afb;
  padding-top: 1rem;
  padding-bottom: 1rem;
  padding-left: 0.5rem;
  padding-right: 0.5rem;
  border-radius: 10px;
}

.messages {
  padding: 0.5rem;
}

.contacts {
  padding: 0.5rem;
}

.contact-container {
  width: auto;
  /* border: 1px solid green; */
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 5px;
  background-color: white;
  padding-top: 1rem;
  padding-bottom: 1rem;
  padding-left: 0.5rem;
  padding-right: 0.5rem;
  border-radius: 10px;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.26);
}

input {
  border-radius: 20px;
  height: 2rem;
  flex-grow: 1;
  border-color: gray;
  border-width: 1px;
  padding-left: 30px;
}

.UserProfilePic {
  height: 2.5rem;
  border-radius: 20px;
  margin-right: 0.5rem;
}

#search-container {
  /* border: 1px solid blue; */
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  padding-left: 4rem;
  padding-right: 4rem;
}
</style>