<template>
  <div class="login_container">
      <div class="login_box">
        <h3 class="title">用户登录</h3>
        <el-form class="el_form" ref="form" :model="form" label-width="80px" :rules="formRules">
          <el-form-item el-form-item label="用户名" prop="username">
            <el-input v-model="form.username" placeholder="输入用户名"></el-input>
          </el-form-item>
          <el-form-item el-form-item label="密码" prop="password">
            <el-input v-model="form.password" placeholder="输入密码" type="password"></el-input>
          </el-form-item>
          <el-form-item label="">
            <el-radio-group v-model="form.type">
              <el-radio label="dormiooryAdmin">宿舍管理员</el-radio>
              <el-radio label="student">学生</el-radio>
            </el-radio-group>
          </el-form-item>
          <el-form-item>
            <el-button class="login_buttom" type="primary" @click="onSubmit" :loading="loading">登录</el-button>
          </el-form-item>
        </el-form>
      </div>
      
  </div>
</template>

<script>
export default {
  name:"Login",
  data() {
    return {
      loading:false,
      form: {
          username: 'admin1',
          password: '123456',
          type: 'student',
      },
      formRules:{
        username:[
          {required: true, message: '请输入用户名称', trigger: 'blur'}
          ],
        password:[
          {required: true, message: '请输入密码', trigger: 'blur'}
          ]
      }
    }
  },
  methods:{
    onSubmit(){
      this.$refs.form.validate((valid)=>{
        if(valid){
          this.loading = true
        }
      })
    }
  }
}
</script>

<style scoped>
.login_box{
  width: 450px;
  height: 350px;
  background-color: #fff;
  border-radius: 3px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
.el_form{
  margin: 20px;
}
.title{
  margin-left: 40px;
}
.login_buttom{
  width: 100px;
}
</style>