<template>
  <form @submit.prevent="handleSubmit">
      <label>پست الکترونیکی:</label>
      <input type="email" autocomplete="username" required v-model="email">

      <label>گذرواژه:</label>
      <input type="password" autocomplete="current-password" required v-model="password">
      <div class="error" v-if="passwordError">{{ passwordError }}</div>
      <label>شغل:</label>
      <select v-model="role">
          <option value="developer">Web Developer</option>
          <option value="designer">Web Designer</option>
      </select>
      
      <label>مهارت ها:</label>
      <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
      <div class="pill" v-for="skill in skills" :key="skill" @click="deleteSkill(skill)">
          {{skill}}
      </div>

      <div class="terms">
        <input type="checkbox" required v-model="terms">
        <label>شرایط و قوانین را می پذیرم</label>
      </div>
      
      <div class="submit">
          <button>ایجاد حساب کاربری</button>
      </div>

  </form>
</template>

<script>
export default {
data(){
    return{
        email: '',
        password: '',
        role:'',
        terms: false,
        tempSkill: '',
        skills: [],
        passwordError: ''
    }
},
methods:{
    addSkill(e){
        if(e.key === ',' && this.tempSkill){
            if(!this.skills.includes(this.tempSkill)){
                this.skills.push(this.tempSkill)
            }
            this.tempSkill = ''
        }
    },
    deleteSkill(skill){
        // this.skills.splice(this.skills.indexOf(skill),1)
        this.skills = this.skills.filter((item) => {
            return item !== skill
        })
    },
    handleSubmit(){
        this.passwordError = this.password.length > 5 ? '' : 'گذرواژه انتخابی می بایست حداقل شامل 6 کاراکتر باشد.'

        if(!this.passwordError){
            console.log('Email: ', this.email);
            console.log('Password: ', this.password);
            console.log('Role: ', this.role);
            console.log('Skills: ', this.skills);
            console.log('Terms: ', this.terms);
        }
    }
}
}
</script>

<style>
form{
    max-width: 420px;
    margin: 30px auto;
    background:  white;
    text-align: right;
    padding: 40px;
    border-radius: 10px;
}
label{
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    font-weight: bold;
}
input, select{
  font-family: IRANSans;
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 0 0 10px;
    position: relative;
    top: 2px;
}
.pill{
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
}
button{
  font-family: IRANSans;
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
}
.submit{
    text-align: center;
}
.error{
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.6em;
    font-weight: bold;
}
</style>