<template>
  <div>
    <strong style="font-size: 2rem;">회원정보 수정</strong>
      <table class="simple_table">
        <tbody>
          <tr>
            <th scope="row">아이디(이메일)</th>
            <td><strong>{{userData.email}}</strong></td>
          </tr>
          <tr>
            <th scope="row">이름</th>
            <td><strong>{{userData.name}}</strong></td>
          </tr>
          <tr>
            <th scope="row">휴대폰 번호</th>
            <td>
              <input type="text" v-model="newphone"><button @click="changePhone">저장</button>

            </td>
          </tr>
          <tr>
            <th scope="row">비밀번호변경</th>
            <td>
              <ChangePassword />
            </td>
          </tr>
        </tbody>
      </table>
  </div>
</template>

<script>
import { mapActions, mapState } from 'vuex'
import ChangePassword from '../../components/accounts/ChangePassword.vue'

export default {
  name: 'UserModify',
  components: {
    ChangePassword,
  },
  computed: {
    ...mapState('accountStore',['userData']),
  },
  data() {
    return {
      newphone: '',
    }
  },

  methods: {
    ...mapActions('accountStore',['UPDATE_PHONE']),
    changePhone: function () {
      this.UPDATE_PHONE({email : this.userData.email, phone : this.newphone})
    }
  },

  created() {
    this.newphone = this.userData.phone
  }
}
</script>

<style scoped>
  .simple_table { 
    width: 75%; 
    border-top: 2px solid #969696;
    border-bottom: 2px solid #969696;
    border-collapse: separate; 
    border-spacing: 1px;
  }
  
  .simple_table th { 
    width: 25%;
    padding: 20px; 
    background: #EEF1F8; 
    font-weight: bold; 
    text-align: left; 
    border-bottom: 1px solid #ddd;
    border-right: 1px solid #ddd;
  }

  .simple_table td { 
    padding: 15px; 
    border: none; 
    border-bottom: 1px solid #ddd;
    text-align: left; 
  }

  table {
    border-right: 1px solid #ddd;
  }

  input {
    height: 32px;
    width: 150px;
    margin-bottom: -1px;
    padding: 0 0 0 5px;
    border: 1px solid #ddd;
    font-size: 16px;
    color: #333;
  }

  button {
    margin: 0 10px;
    padding: 4px 8px;
    padding-bottom: 3px;
    border: 1px solid #999;
    color: #333;
    border-radius: 1px;
    box-shadow: 0 -2px 0 rgb(0 0 0 / 10%) inset;
    font-size: 14px;
  }
  
</style>