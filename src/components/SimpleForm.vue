<template>
  <div class="form-container">
    <h1>Hiring Form</h1>
    <Form @submit="submitForm" :validation-schema="schema">
      <Field name="firstName" v-slot="{ handleChange }">
        <base-input v-model="formData.firstName" @update:modelValue="handleChange" placeholder="First Name">
          <template #title>
            <h4>
              First Name
            </h4>
          </template>
          <template #error>
              <ErrorMessage name="firstName" as="span" />
          </template>
        </base-input>
      </Field>
      <Field name="lastName" v-slot="{ handleChange }">
        <base-input v-model="formData.lastName" @update:modelValue="handleChange" placeholder="Last Name">
          <template #title>
            <h4>
              Last Name
            </h4>
          </template>
          <template #error>
            <ErrorMessage name="lastName" as="span" />
          </template>
        </base-input>
      </Field>
      <Field name="description" v-slot="{ handleChange }">
        <base-textarea v-model="formData.description" @update:modelValue="handleChange" placeholder="Description">
          <template #title>
            <h4>
              Your description
            </h4>
          </template>
          <template #error>
            <ErrorMessage name="description" as="span" />
          </template>
        </base-textarea>
      </Field>
      <Field name="gender" v-slot="{ handleChange }">
        <base-select v-model="formData.gender" :options="genderOptions" @update:modelValue="handleChange" placeholder="Gender">
          <template #title>
            <h4>
              Please specify your gender
            </h4>
          </template>
          <template #error>
            <ErrorMessage name="gender" as="span" />
          </template>
        </base-select>
      </Field>
      <Field name="jobType" v-slot="{ handleChange }">
         <h4 class="job-title">
          What kind of job do you want to apply?
        </h4>
          <div id="radio-buttons">
            <base-radio
              v-model="formData.jobType"
              label="Full Time"
              value="Full Time"
              @update:modelValue="handleChange"
            />
            <base-radio
              v-model="formData.jobType"
              label="Part Time"
              value="Part Time"
              @update:modelValue="handleChange"
            />
          </div>
        <ErrorMessage name="jobType" as="span" />
      </Field>
      <Field name="acceptedTerms" v-slot="{ handleChange }">
        <div id="terms">
          <base-checkbox v-model="formData.acceptedTerms" label="Accept Terms and Conditions" @update:modelValue="handleChange" />
        </div>
        <ErrorMessage name="acceptedTerms" as="span" />
      </Field>
      <button type="submit">
        Submit
      </button>
    </Form>
  </div>
</template>

<script>
import { Form, Field, ErrorMessage } from 'vee-validate';
import * as yup from 'yup';
import BaseInput from './BaseInput';
import BaseCheckbox from './BaseCheckbox';
import BaseTextarea from './BaseTextarea';
import BaseSelect from './BaseSelect';
import BaseRadio from './BaseRadio';
  export default {
    name: 'SimpleForm',
    components: {
      BaseCheckbox,
      BaseInput,
      BaseTextarea,
      BaseSelect,
      BaseRadio,
      Form,
      Field,
      ErrorMessage
    },
    data() {
      const schema = yup.object({
        firstName: yup.string().required('Please provide your first name'),
        lastName: yup.string().required('Please provide your last name'),
        description: yup.string().required('Please provide your description'),
        gender: yup.string().required('Please specify your gender'),
        jobType: yup.string().required('Please specify your job type'),
        acceptedTerms: yup.boolean().isTrue('Please accept the terms and conditions').required('Please accept the terms and conditions')
      });
      return {
        formData: {
          firstName: '',
          lastName: '',
          description: '',
          gender: '',
          jobType: '',
          acceptedTerms: false,
        },
        genderOptions: ['Male', 'Female', 'Other'],
        schema
      }
    },
    methods: {
      submitForm() {
        console.log(this.formData);
      },
    },
  }
</script>

<style scoped>
  .form-container {
    max-height: 700px;
    overflow: auto;
    border: 1px solid rgb(249, 229, 186);
    padding: 20px;
    box-shadow: 2px 1px 5px 0.5px;
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
  }

  .form-container h1 {
    text-align: center;
    font-size: 50px;
    font-weight: 600;
  }

  .form-container form {
    display: flex;
    width: 400px;
    flex-direction: column;
    align-items: center;
  }

  .form-container form div {
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  .form-container form div h4 {
    font-size: 20px;
    color: rgb(74, 76, 77);
  }

  .job-title {
    font-size: 20px;
    font-weight: normal;
  }

  button {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 50px;
    font-weight: bold;
    font-size: 20px;
    cursor: pointer;
    background: rgb(210, 204, 191);
    border: 1px solid rgb(182, 182, 181);
    width: 100%;
    border-radius: 10px;
    transition: all 0.5s ease-in-out;
  }

  button:hover {
    background: rgb(156, 150, 138);
  }

  span {
    color: red;
  }

  #radio-buttons {
    display: flex;
    flex-direction: row;
  }

  #terms {
    display: flex;
    flex-direction: row;
  }
</style>