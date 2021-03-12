<style scoped>
.bright{
  background: #34f839;
}
.dark{
  background: #f8f8f9;
}
</style>

<template>
  <div class="dark" style="height: 100%">
    <table style="width: 100%;height: 100%">
      <tr>
        <td valign="middle" align="center">
          <Card style="width:320px">
            <div style="text-align:center">
              <span style="font-size: 28px"><Icon type="md-cloud-outline" size="30"/> FileMarker</span>
              <br>
              <br>
              <Form ref="formInline" :model="formInline" :rules="ruleInline" inline>
                <FormItem prop="user">
                  <Input type="text" v-model="formInline.user" placeholder="Username">
                    <Icon type="ios-person-outline" slot="prepend"></Icon>
                  </Input>
                </FormItem>
                <FormItem prop="password">
                  <Input type="password" v-model="formInline.password" placeholder="Password">
                    <Icon type="ios-lock-outline" slot="prepend"></Icon>
                  </Input>
                </FormItem>
                <FormItem style="alignment: right">
                  <Button type="primary" @click="handleSubmit('formInline')">登录</Button>
                </FormItem>
              </Form>
            </div>
          </Card>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'login',
  data () {
    return {
      formInline: {
        user: 'admin',
        password: ''
      },
      ruleInline: {
        user: [
          { required: true, message: '请输入用户名', trigger: 'blur' }
        ],
        password: [
          // { required: true, message: 'Please fill in the password.', trigger: 'blur' },
          // { type: 'string', min: 6, message: 'The password length cannot be less than 6 bits', trigger: 'blur' }
        ]
      }
    }
  },
  methods : {
    handleSubmit(name) {
      // this.login();
      this.$refs[name].validate((valid) => {
        if (valid) {
          // this.$Message.success('Success!');
          this.login();
        } else {
          this.$Message.error('Fail!');
        }
      })
    },
    login() {
      this.$parent.user=this.user;
      this.$goRoute("/index");
    }
  }
}
</script>
