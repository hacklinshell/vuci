<template>
    <div @keydown.enter="handleSubmit">
        <Card class="login-container">
            <p slot="title">Authorization Required</p>
            <Form ref="form" :model="form" :rules="ruleValidate">
                <FormItem prop="username">
                    <Input type="text" v-model="form.username" auto-complete="off" placeholder="Enter username...">
                        <Icon type="ios-person-outline" slot="prepend"></Icon>
                    </Input>
                </FormItem>
                <FormItem>
                    <Input type="password" v-model="form.password" auto-complete="off" placeholder="Enter password...">
                        <Icon type="ios-locked-outline" slot="prepend"></Icon>
                    </Input>
                </FormItem>
                <FormItem>
                    <Button type="primary" style="width:100%;" @click="handleSubmit">Login</Button>
                </FormItem>
            </Form>
        </Card>
    </div>
</template>

<script>
    export default {
        name: 'Login',
        data() {
            return {
                form: {
                    username: '',
                    password: ''
                },
                ruleValidate: {
                    username: [
                        {required: true, trigger: 'blur'}
                    ]
                }
            }
        },
        methods: {
            handleSubmit() {
                var v = this;
                this.$refs['form'].validate((valid) => {
                    if (valid) {
                        v.$ubus.login(this.form.username, this.form.password).then((r) => {
                            if (r)
                                v.$router.push('/');
                        }, () => {
                            console.log('Login Fail!');
                        });
                    } else {
                        console.log('Login Fail!');
                    }
                });
            }
        }
    }
</script>

<style scoped>
    .login-container {
        width: 400px;
        height: 240px;
        position: absolute;
        top: 50%;
        left: 50%;
        margin-left: -200px;
        margin-top: -120px;
    }
</style>
