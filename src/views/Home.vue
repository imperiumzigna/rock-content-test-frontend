<template>
  <div class="home">
    <vs-sidebar
      default-index="1"
      color="primary"
      class="sidebarx"
      spacer
      position-right
      v-model="active"
    >
      <div class="header-sidebar" slot="header">
        <h4>NOVO MEMBRO</h4>
      </div>
      <vs-sidebar-item index="0">
        <vs-input icon="person" type="text" label-placeholder="Nome" v-model="name"/>
      </vs-sidebar-item>
      <vs-sidebar-item index="1">
        <vs-input icon="email" type="email" name="email" label-placeholder="Email" v-model="email"/>
      </vs-sidebar-item>
      <vs-spacer/>
      <vs-sidebar-item index="2">
        <vs-button color="success" type="filled" @click="addUser">Criar membro da equipe</vs-button>
      </vs-sidebar-item>
    </vs-sidebar>
    <!-- Add row with 12 col -->
    <tab-nav/>
    <vs-tabs>
      <vs-tab vs-label="Minha Equipe">
        <div>
          <vs-row vs-type="flex" vs-justify="flex-start">
            <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="4">
              <el-input
                placeholder="Digite uma palavra-chave e tecle enter para buscar."
                clearable
                prefix-icon="el-icon-search"
                v-model="search"
              ></el-input>
            </vs-col>
            <vs-col
              vs-type="flex"
              vs-justify="flex-end"
              vs-align="center"
              vs-lg="2"
              vs-sm="2"
              vs-xs="12"
              vs-w="4"
            >
              <label>Visualizar:</label>
            </vs-col>
            <vs-col
              vs-type="flex"
              vs-justify="flex-end"
              vs-align="center"
              vs-lg="2"
              vs-sm="2"
              vs-xs="12"
              vs-w="2"
            >
              <el-switch
                v-model="switchFreelasOrUsers"
                active-text="Usuários"
                inactive-text="Freelas"
              ></el-switch>
            </vs-col>
            <vs-col
              vs-type="flex"
              vs-justify="flex-end"
              vs-align="center"
              vs-lg="2"
              vs-sm="4"
              vs-xs="12"
              vs-w="2"
            >
              <vs-button color="success" @click="active=!active" type="filled">NOVO MEMBRO</vs-button>
            </vs-col>
          </vs-row>
          <br>
          <vs-row vs-align="left" vs-type="flex" vs-justify="left" vs-w="12">
            <vs-col
              v-for="user in usersData"
              vs-type="flex"
              vs-justify="left"
              vs-align="left"
              vs-w="3"
              vs-lg="3"
              vs-sm="4"
              vs-xs="12"
              :key="user.id"
            >
              <user-card @edit_user="editUser" :user="user"/>
            </vs-col>
          </vs-row>
        </div>
      </vs-tab>
      <vs-tab vs-label="Service">
        <div class>Tab</div>
      </vs-tab>
      <vs-tab vs-label="login">
        <div class>Tab</div>
      </vs-tab>
    </vs-tabs>
    <!-- Modal edit user -->
    <div class="centerx">
      <vs-popup class="editpopup" title="Editar Usuário" :active.sync="popupActivo">
        <vs-row>
          <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="12">
            <vs-input
              icon="person"
              type="text"
              :value="editingUser.name"
              v-model="editingUser.name"
              label-placeholder="Nome"
            />
          </vs-col>

          <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="12">
            <vs-input
              icon="email"
              type="email"
              :value="editingUser.email"
              v-model="editingUser.email"
              label-placeholder="Email"
            />
          </vs-col>
          <vs-col>
            <vs-button
              color="success"
              :value="editUser.id"
              type="filled"
              @click="saveEditUser"
            >Salvar Edição</vs-button>
          </vs-col>
        </vs-row>
      </vs-popup>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import NavBar from "@/components/NavBar.vue";
import UserCard from "@/components/UserCard.vue";
import TabNav from "@/components/TabNav.vue";
const users = [
  {
    id: 0,
    name: "Aline Costa de Oliveira",
    email: "aline.costa@rockcontent.com",
    image_url: "https://randomuser.me/api/portraits/women/1.jpg"
  },
  {
    id: 1,
    name: "Bruno Pontes",
    email: "bruno.pontes@rockcontent.com",
    image_url: "https://randomuser.me/api/portraits/men/1.jpg"
  },
  {
    id: 2,
    name: "Carla Alves Martins",
    email: "carla@rockcontent.com",
    image_url: "https://randomuser.me/api/portraits/women/2.jpg"
  },
  {
    id: 3,
    name: "Daniel Henrique Corrêa",
    email: "daniel.henrique@rockcontent.com",
    image_url: "https://randomuser.me/api/portraits/men/5.jpg"
  }
];

export default {
  name: "home",
  components: { UserCard, TabNav },
  data() {
    return {
      search: "",
      active: false,
      name: "",
      email: "",
      editingUser: {
        id: 0,
        name: "",
        email: "teste",
        image_url: ""
      },
      nameNotValid: false,
      popupActivo: false,
      emailNotValid: false,
      switchFreelasOrUsers: "",
      usersData: users
    };
  },
  methods: {
    addUser() {
      const newId = this.usersData.length + 1;

      this.usersData = [
        ...this.usersData,
        {
          id: newId,
          name: this.name,
          email: this.email,
          image_url: `https://randomuser.me/api/portraits/men/${newId}.jpg`
        }
      ];
      this.$vs.notify({
        title: "Mensagem!",
        text: "Membro adicionado a equipe com sucesso"
      });
    },
    editUser(id) {
      const user = this.usersData.filter(user => user.id == id).pop();
      this.editingUser = user;
      this.popupActivo = true;
    },
    saveEditUser() {
      const editUser = this.editingUser;
      const users = this.usersData.map(function(item) {
        return item.id == editUser.id ? editUser : item;
      });
      this.usersData = users;
      this.$vs.notify({
        title: "Mensagem!",
        text: "Usuário alterado com sucesso"
      });
    }
  },
  watch: {
    search(filterValue = "") {
      if (filterValue == "") {
        this.usersData = users;
      }
      const filter = searchKey =>
        searchKey.name.includes(filterValue) ||
        searchKey.email.includes(filterValue);
      this.usersData = users.filter(filter);
    }
  }
};
</script>


<style>
.home {
  width: 100%;
}
.editpopup .vs-input {
  float: left;
  width: 100%;
  margin: 10px;
  margin-top: 5px;
}
.a-icon {
  outline: none;
  text-decoration: none !important;
  display: flex;
  align-items: center;
  justify-content: center;
}

.a-icon i {
  font-size: 18px;
}
</style>