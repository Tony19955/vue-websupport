<template>
  <div id="q-app">
    <div class="main-container">

      <!-- Coupon input -->
      <div class="input-container">
        <q-input class="input-default input-w-btn" 
          square outlined
          v-model="coupon"       
          label="Sem vložte kupón"
          :rules="[val => val !== 'JFHSO4663J' || 'Tento kupón platí pre hosting do 3GB']"
        />       
        <button class="add-btn">+</button>
      </div>
      
      <!-- Telephone input -->
      <div class="input-container">
        <q-input class="input-default" 
          list="tel-preselection"
          square outlined
          v-model="phone"
          type="tel"
          mask="(###) ### ### ###" 
          label="Telefónne číslo"        
        >
          <template v-slot:prepend>
            <datalist id="tel-preselection" class="tel-preselection">
              <option value="+421" />
              <option value="+420" />
            </datalist>
          </template>

          <template v-slot:append> 
            <span v-if="required === true" class="not-required">(nepovinné)</span>
          </template>
          
        </q-input>
      </div>

      <!-- Login input -->
      <div class="input-container">
        <q-input class="input-default" 
          square outlined
          v-model="text" 
          :error="!isValid"
          label="Prihlasovacie meno / Login"
        >
          <template v-slot:error>
            Toto prihlasovacie meno je už obsadené. Zvoľte si prosím iné.
          </template>

        </q-input>
      </div>

      <!-- Search input -->
      <div class="input-container">
        <q-input dark class="input-default" 
          color="positive" 
          bg-color="dark"          
          label-color="primary"
          square outlined
          v-model="search"  
          label="Invoice search">

          <template v-slot:append>
            <q-icon v-if="text !== ''" name="close" @click="text = ''" class="cursor-pointer"></q-icon>
            <q-icon color="primary" name="search"></q-icon>
          </template>

        </q-input>
      </div>

      <!-- Email input -->
      <div class="input-container">
        <q-input class="input-default"                        
          autogrow           
          square outlined
          v-model="emails"          
          label="Emails (comma separated)"
          :rules="[val => val && val.length > 0 || 'Field is required']"
        />   
      </div>
      
    </div>    
  </div>
</template>

<script >
export default {
  name: 'App',  
  data () {
    return {
      coupon: '',
      search: '',
      emails: '',
      text: '',
      phone: '',
      required: true,
    }  
  },
  computed: {
    isValid () {
      return this.text !== 'webadmin3'
    }
  }  
}
</script>

<style lang="scss"> 

  /* Colors */
  $ws-white: #ffffff;
  $ws-black: #000000;
  $ws-snow: #f9f9f9; /* #f9fafb */
  $ws-white-smoke: #f2f2f5; /* #eef0f3 */
  $ws-isabelline: #e2e5e9; /* #e4e7e9, #e8e8ea, #b8babc */
  $ws-lighter: #d4d7d9;
  $ws-light: #bec2c4;
  $ws-light-gray: #bbc7d3; /* #b1bcc6 */
  $ws-light-slate-gray: #6f7c8d; /* #666666 */
  $ws-stale-gray: #80878d;
  $ws-dark-gray: #949a9e;
  $ws-davys-gray: #3c424c;
  $ws-char-coal: #2b3339; /* #3b4a59 */
  $ws-medium-jungle-gray: #242628; /* #131921 */
  $ws-dark-blue: #2c3742;
  $ws-blue: #1083ff;
  $ws-aqua: #9ececa;
  $ws-purple: #383052;
  $ws-coral-red: #f82b3a;
  $ws-red: #dd5656;
  $ws-mikado-yellow: #eeae12;
  $ws-orange: #e4aa34;
  $ws-emerald: #43b574;
  $ws-green: #80c700;

  $ws-primary: #1083ff;
  $ws-secondary: $ws-isabelline;
  $ws-accent: #fc464a;

  * { 
    margin: 0;
    padding: 0;
    border: 0;
    outline: 0;
    box-sizing: border-box;
  }

  .main-container {   
    width: 100%; 
    margin-top: 2rem;
    display: flex;
    flex-direction: column;  
    align-items: center;

    .input-container {      
      width: 25%;
      margin: 2rem 0;
      display: flex;
      justify-content: center; 
      align-items: center;
    }

    .q-input {
      height: 42px;
    }
    
    .input-default {      
      font-size: .8rem;
      font-weight: normal;
      width: 100%;
      min-height: 2.625rem;            
    }  

    .q-field--with-bottom {
      padding-bottom: 0;
    }

    .q-field__label {
      font-size: .9rem;
    }

    .input-w-btn {
      border-right: none;
    }

    .not-required {
      font-size: .8rem;
    }   

    .add-btn {
      height: 56px;
      color: $ws-snow; 
      font-size: 2rem;
      padding: 0 1.3rem;
      font-weight: 300;
      background: $ws-char-coal;
      cursor: pointer;
    }  
    
    .tel-preselection {
      width: 2rem;
    }

    .uppercase {
      text-transform: uppercase;
    }
  }

</style>
