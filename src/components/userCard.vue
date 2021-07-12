<template>
  <div class="user-card">
    <h1>Научу зарабатывать</h1>
    <div class="main-information">
      <img src="../assets/img/man.jpg" />
      <div class="info">
        <h2>
          {{ getAuthorFullName + getAuthorFullName }}
        </h2>
        <strong>Бизнес-коуч</strong>
        <ul>
          <li>Учу людей зарабатывать бабки</li>
          <li>Еще текст</li>
          <li>И еще</li>
        </ul>
      </div>
    </div>
    <p>Участников: {{ users.length }}</p>
    <ul>
      <li
       v-for="(user, index) in users"
       :key="index"
      >
        {{ `${index +1} ${getFullName(user)}` }}
      </li>
    </ul>
    <button
      type="button"
      @click="currentPage--"
    >
      Пред.
    </button>
    <button
      v-for="page in pages"
      :key="page"
      type="button"
      @click="currentPage = page"
    >
      {{ page }}
    </button>
    <button
      type="button"
      @click="currentPage++"
    >
      След.
    </button>
    <p>Страница {{ currentPage }} из {{ pages }}</p>
  </div>
</template>

<script>
export default {
  name: "userCard",
  data() {
    return {
      firstName: "Игнатий",
      secondName: "Иларионович",
      lastName: "Богатов",
      users: [
        {
          firstName: "Иван",
          secondName: "Иванович",
          lastName: "Иванов",
        },
        {
          firstName: "Иван",
          secondName: "Иванович",
          lastName: "Иванов",
        },
        {
          firstName: "Иван",
          secondName: "Иванович",
          lastName: "Иванов",
        },
      ],
      pages: 3,
      currentPage: 1
    };
  },
  computed: {
    getAuthorFullName() {
      return `${this.firstName} ${this.secondName} ${this.lastName}`.toUpperCase();
    },
  },
  methods: {
    getFullName(user) {
      return `${user.firstName} ${user.secondName} ${user.lastName}`;
    },
    loadUsers(page) {
      console.log(`Загрузка пользователей страница ${page}`)
    }
  },
  watch: {
    currentPage(page) {
      this.loadUsers(page)
    }
  }
};
</script>
