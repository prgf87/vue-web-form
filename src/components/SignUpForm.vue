<template>
  <form>
    <label>Email: </label>
    <input type="email" required v-model="email" />

    <label>Password: </label>
    <input type="password" required v-model="password" />

    <label>Role: </label>
    <select v-model="role">
      <option value="Designer">Web Designer</option>
      <option value="Developer">Web Developer</option>
    </select>

    <label>Skills</label>
    <input type="text" v-model="tempSkill" />

    <div class="terms">
      <input type="checkbox" required v-model="terms" />
      <label>Accept terms & conditions</label>
    </div>
  </form>
  <div class="container">
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms accepted: {{ terms }}</p>
    <p>Names: {{ names }}</p>
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
    };
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
  border-bottom: 1px solid #ddd;
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
</style>
