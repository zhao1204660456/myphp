<template>
    <div class="box">
        <el-form ref="form" :rules="rules" :model="form" label-width="80px" class="demo-ruleForm">
            <el-form-item label="用户名" prop="username">
                <el-input v-model="form.username"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input v-model="form.password" type="password" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="角色" prop="check">
                <el-select v-model="form.check" placeholder="请选角色">
                    <el-option label="管理员" value="admin"></el-option>
                    <el-option label="教师" value="teacher"></el-option>
                    <el-option label="学生" value="student"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitForm('form')">登录</el-button>
                <el-button @click="resetForm('form')">重置</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
    export default {
        name: "login",
        data() {
            return {
                form: {
                    username: '',
                    password:'',
                    check:''
                },
                rules: {
                    username: [
                        {required: true, message: '请输入用户名', trigger: 'blur'},
                        {min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur'}
                    ],
                    password:[
                        {required: true, message: '请输入用户密码', trigger: 'blur'},
                    ],
                    check:[
                        {required: true, message: '请选择角色', trigger: 'blur'},
                    ]
                }
            }
        },
        methods: {
            submitForm(formName) {
                this.$refs[formName].validate((valid) => {
                    if (valid) {
                        this.$router.push({name:'index'});
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            },
            resetForm(formName) {
                this.$refs[formName].resetFields();
            }
        }
    }
</script>

<style scoped>
    .box{
        margin: 0 auto;
        width: 300px;
        height: 300px;
    }
</style>