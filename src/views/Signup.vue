<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Signup Page</h1>
        <v-form>
          <v-text-field
            label="Email"
            type="email"
            v-model="email"
            :rules="emailRules"
          ></v-text-field>
          <v-autocomplete
            label="Which browser do you use?"
            :items="browsers"
          ></v-autocomplete>
          <v-file-input label="Attach profile picture"></v-file-input>
          <v-text-field label="Birthday" v-model="birthday" readonly />
          <v-date-picker v-model="birthday" />
          <v-checkbox
            label="Agree to terms & conditions"
            v-model="agreeToTerms"
            :rules="agreeToTermsRules"
            required
          ></v-checkbox>
          <v-btn type="submit" color="primary">Submit</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      birthday: '',
      browsers: ['Chrome', 'Firefox', 'Safari', 'Edge', 'Brave'],
      agreeToTerms: false,
      agreeToTermsRules: [
        (value) =>
          !!value ||
          'You must agree to the terms and conditions to sign up for an account.',
      ],
      email: '',
      emailRules: [
        (value) => value.indexOf('@') !== 0 || 'Email should have a username.',
        (value) => value.includes('@') || 'Email should include an @ symbol.',
        (value) =>
          value.indexOf('.') - value.indexOf('@') > 1 ||
          'Email should contain a valid domain.',
        (value) =>
          value.includes('.') || 'Email should include a period symbol.',
        (value) =>
          value.indexOf('.') <= value.length - 3 ||
          'Email should contain a valid domain extension.',
      ],
    };
  },
};
</script>

<style></style>
