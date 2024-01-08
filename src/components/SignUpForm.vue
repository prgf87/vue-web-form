<template>
  <form @submit.prevent="handleSubmit">
    <label>Email: </label>
    <input type="email" v-model="email" />

    <label>Password: </label>
    <input type="password" v-model="password" />
    <div v-if="passwordError" class="p-error">
      {{ passwordError }}
    </div>

    <label>Role: </label>
    <select v-model="role">
      <option value="Designer">Web Designer</option>
      <option value="Developer">Web Developer</option>
    </select>

    <label>Skills</label>
    <input
      type="text"
      v-model="tempSkill"
      @keyup="addSkill"
      value="tempSkill"
    />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">
        {{ skill.slice(0, -1) }}
      </span>
    </div>
    <div class="terms">
      <input type="checkbox" v-model="terms" />
      <label>Accept terms & conditions</label>
    </div>
    <div class="submit">
      <button>Create Account</button>
    </div>
  </form>
  <div class="container">
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms accepted: {{ terms }}</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      skills: [],
      tempSkill: "",
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkill = "";
      }
    },
    deleteSkill(skill) {
      // this.skills.splice(i, 1);
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    handleSubmit() {
      this.passwordError =
        this.password.length > 5
          ? ""
          : "Password must be at least 6 characters long";
      if (!this.passwordError) {
        console.log(
          this.email,
          this.password,
          this.role,
          this.skills,
          this.terms
        );
      }
    },
  },
};
</script>
<style>
form {
  max-width: 420px;
  margin: 10px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 10px;
  font-size: 0.9em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border: 1px solid #ddd;
  border-radius: 8px;

  color: #555;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 6px 0 0;
  position: relative;
  top: 4px;
}
.container {
  text-align: left;
  max-width: 420px;
  margin: 0px auto;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}
button {
  background: #888;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 14px;
  letter-spacing: 0.5px;
  cursor: pointer;
  margin: 30px 0 auto;
  font-weight: 750;
}
.submit {
  text-align: center;
}
.p-error {
  color: red;
  font-size: 12px;
  margin: 10px 0;
  font-weight: bold;
}
</style>
