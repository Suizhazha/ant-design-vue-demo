<template>
  <div id="app">
      <a-form id="components-form-demo-normal-login"
              :form="form"
              class="login-form"
              @submit="onSubmit"
      >
        <a-form-item>
          <a-input
              v-decorator="[
          'userName',
          { rules: [{required: true,message: '你没写用户名！！！'}] },
        ]"
              placeholder="Username"
          >
            <a-icon slot="prefix" type="user" style="color: rgba(0,0,0,.25)" />
          </a-input>
        </a-form-item>


        <a-form-item>
          <a-input
              v-decorator="[
          'password',
          { rules: [{ required: true, message: '你没写密码！！！' }] },
        ]"
              type="password"
              placeholder="Password"
          >
            <a-icon slot="prefix" type="lock" style="color: rgba(0,0,0,.25)" />
          </a-input>
        </a-form-item>


          <a-button type="primary" html-type="submit" class="login-form-button">
            Log in
          </a-button>

      </a-form>
  </div>
</template>

<script>
export default {
  beforeCreate() {
    this.form = this.$form.createForm(this, { name: 'normal_login' });
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
  },
};
</script>


<style>
#components-form-demo-normal-login .login-form {
  max-width: 300px;
}
#components-form-demo-normal-login .login-form-forgot {
  float: right;
}
#components-form-demo-normal-login .login-form-button {
  width: 100%;
}
</style>