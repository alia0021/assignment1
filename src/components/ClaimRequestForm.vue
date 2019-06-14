<template>
  <!-- created claim request form component and import element form -->
  <div>
    <!-- add my dialog box -->
    <el-dialog
      title="Contact request form information"
      :visible.sync="dialogVisible"
      width="30%"
      :before-close="handleClose"
    >
      <!-- add my ruleForm information to my dialog p -->
    <p> First Name: {{ruleForm.firstName}}</p>
   <p> Last Name: {{ruleForm.lastName}}</p>
    <p> Email: {{ruleForm.email}}</p>
    <p>Subject: {{ruleForm.subject}}</p>
   <p> Content: {{ruleForm.content}}</p>
    <p>I agree to the terms: true </p> 
    <!-- agree to terms will always be true therefore i just wrote true. without pulling from the ruleForm. -->

  


      </span>
    </el-dialog>
    <!--v-show will only show my form if my dialogvisible is false -->
    <el-form
      v-show="!dialogVisible"
      :model="ruleForm"
      :rules="rules"
      ref="ruleForm"
      label-width="220px"
      class="demo-ruleForm"
    >
      <h1>Claim Request Form</h1>
      <el-form-item label="First Name" prop="firstName">
        <!-- input First name and property -->
        <el-input v-model="ruleForm.firstName"></el-input>
      </el-form-item>
      <el-form-item label="Last Name" prop="lastName">
        <!-- input Last name and property -->
        <el-input v-model="ruleForm.lastName"></el-input>
      </el-form-item>
      <el-form-item label="Email" prop="email">
        <!-- input email  and property -->
        <el-input v-model="ruleForm.email"></el-input>
      </el-form-item>
      <el-form-item label="Subject" prop="subject">
        <el-input type="text" v-model="ruleForm.subject"></el-input>
      </el-form-item>
      <el-form-item label="Claim Content" prop="content">
        <el-input
          type="textarea"
          placeholder="Input additional information here."
          v-model="ruleForm.content"
        ></el-input>
      </el-form-item>
      <el-form-item prop="type">
        <el-checkbox
          label="Please agree to Terms and Conditions"
          name="type"
          v-model="ruleForm.type"
        ></el-checkbox>
      </el-form-item>
      <el-form-item>
        <el-button @click="submitForm('ruleForm')">Submit</el-button>
      </el-form-item>
    </el-form>
  </div>
  <!-- add form from elementui -->
</template>

<script>
export default {
  data() {
    return {
      // add my dialog info
      dialogVisible: false,
      // add my list of information
      ruleForm: {
        firstName: "",
        lastName: "",
        email: "",
        type: [],
        subject: "",
        content: ""
      },
      rules: {
        // add my rules for my data
        firstName: [
          {
            required: true,
            message: "Please input your first name",
            trigger: "blur"
          },
          {
            min: 3,
            max: 10,
            message: "Length should be 3 to 10",
            trigger: "blur"
          }
        ],
        lastName: [
          {
            required: true,
            message: "Please input your last name",
            trigger: "blur"
          },
          {
            min: 3,
            max: 10,
            message: "Length should be 3 to 10",
            trigger: "blur"
          }
        ],
        email: [
          {
            required: true,
            message: "Please input your email",
            trigger: "blur"
          }
        ],

        type: [
          {
            type: "array",
            required: true,
            message: "Please agree to terms and conditions"
          }
        ],
        subject: [
          {
            required: true,
            message: "Please input your subject",
            trigger: "change"
          }
        ],
        content: [
          {
            required: true,
            message: "Please input your message",
            trigger: "blur"
          }
        ]
      }
    };
  },
  methods: {
    // input my validations for my inputs and data
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          this.dialogVisible = true;
        } else {
          this.dialogVisible = false;
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
};
</script>
