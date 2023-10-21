<template>
  <form>
    <label>Email</label>
    <input type="email" required v-model="email">
    <label>Password</label>
    <input type="password" required v-model="pass">
    <label>Role:</label>
    <select v-model="role">
      <option value="dev">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <br>
    <label>Skills</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
      {{ skill }}
    </div>


    <div class="terms">
      <label>
        <input type="checkbox" required v-model="terms">
        Accept Terms and conditions
      </label>
    </div>

    <div class="">
      <input type="checkbox" v-model="names" value="Shawn">
      <label>Shawn</label>
    </div>

    <div class="">
      <input type="checkbox" v-model="names" value="Yoshi">
      <label>Yoshi</label>
    </div>

    <div class="">
      <input type="checkbox" v-model="names" value="Mario">
      <label>Mario</label>
    </div>

    <div class="">
      <input type="checkbox" v-model="names" value="Zecas">
      <label>Zecas</label>
    </div>

  </form>
  <hr>
  <p>Email : {{ email }}</p>
  <p>Password : {{ pass }}</p>
  <p>Role : {{ role }}</p>
  <p>Terms Accepted: {{ terms }}</p>
  <p>Names: {{ names }}</p>
  <p>Skills: {{ skills }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: 'Mario',
      pass: '',
      role: 'designer',
      terms: false,
      names : [],
      tempSkill: '',
      skills: []
    }
  },
  methods: {
    addSkill(e) {
      console.log(e)
      if( e.key === ',' && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)){
          this.tempSkill = this.tempSkill.slice(0, -1);
          this.skills.push(this.tempSkill)    
        }
        this.tempSkill= ''
      }
    },
  },
}
</script>

<style>

    form {
        max-width: 420px;
        margin: 30px auto;
        background: white;
        text-align: left;
        padding: 40px;
        border-radius: 10px;
    }
    label {
        color: #aaa;
        display: inline-block;
        margin: 25px 0 15px;
        font-size: 0.6em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
    }
    input {
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
      margin: 0 10px 0 0;
      position: relative;
      top: 2px;
    }
</style>