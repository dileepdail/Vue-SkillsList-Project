# Vue-SkillList-Project
A simple Skills List App in Vue JS

## Installing Vue

###### Method 1: Installing Vue through a CDN
1. Create directory vue-cdn  
        mkdir vue-cdn && cd vue-cdn  
2. Create index.html  
3. Add the code in the index.html file

        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>Document</title>
        </head>
        <body>
            <div id="app">
                {{ message }}
            </div>
            <script src="https://cdn.jsdelivr.net/npm/vue@2.5.13/dist/vue.js"></script>
            <script>
                var app = new Vue({
                    el: '#app',
                    data: {
                        message: 'Hello Vue!'
                    }
                })

            </script>
        </body>
        </html>
        
###### Method 2: Install Vue through NPM
 
1. Create directory vue-npm  
      mkdir vue-npm && cd vue-npm
2. Create a package.json file  
      npm init -y
3. Use npm to install vue  
      npm install vue --save
      
###### Method 3: Installing Vue with the Vue CLI

1. You first need to install the Vue CLI:  
    npm install -g @vue/cli
    
2. Create project  
    vue create vue-skills  
    choose default  
    select npm

3. Run Project
    cd vue-skills  
    npm run serve
    
## Vue Templating

###### Vue Interpolation

1. Interpolation in Attributes

        <template>
          <div class="hello">
           {{ name }}
          </div>
        </template>

        <script>
        export default {
          name: 'Skills',
          data() {
            return {
              name: 'Dileep'
            }
          }
        }
        </script>
        
2. Interpolation in Attributes

        <button v-on:click="changeName" v-bind:disabled="btnState">Change Name</button>
        
        data() {
            return {
              name: 'Coursetro',
              btnState: true       // Add this
            }
          },

3. Expressions in Interpolation

        <h1 v-once>{{name}}</h1>

        <!-- Add this -->
        {{ btnState ? 'The button is disabled' : 'The button is active'}}

        <button v-on:click="changeName" v-bind:disabled="btnState">Change Name</button>
        
4. Vue Directives  

*Here is a list of directives that you can use:*

* v-text
* v-html
* v-show
* v-if
* v-else
* v-else-if
* v-for
* v-on
* v-bind
* v-model
* v-pre
* v-cloak
* v-once

## Vue Styling

1. Add sample style code in Skills.vue file

        <style scoped>

          .holder {
            background: #fff;
          }

          ul {
            margin: 0;
            padding: 0;
            list-style-type: none;
          }

          ul li {
            padding: 20px;
            font-size: 1.3em;
            background-color: #E0EDF4;
            border-left: 5px solid #3EB3F6;
            margin-bottom: 2px;
            color: #3E5252;
          }

          p {
            text-align:center;
            padding: 30px 0;
            color: gray;
          }

          .container {
            box-shadow: 0px 0px 40px lightgray;
          }

        </style>
     
2. Add sample style code in App.vue

        <style>
        @import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');

        body {
          background-color: #EEEEEE;
          font-family: 'Montserrat', sans-serif;
          display: grid;
          grid-template-rows: auto;
          justify-items: center;
          align-items: center;
        }
        body, html {
          margin: 0;
          height: 100%;
        }
        #app {
            width: 50%;
        }
        </style>

## Vue Forms

1. Add form in the template area

        <form @submit.prevent="addSkill">
                <input type="text" placeholder="Enter a skill you have.."  v-model="skill">
        </form>
2. Add method in Scripts section

          // Add this section:
          methods : {
              addSkill(){
                  this.skills.push({skill: this.skill});
                  this.skill = '';
              }
          }

###### Vue Form Validation
1. install validator in the project  
        npm add vee-validate
        
2. Import vee-validate in main.js file

        import VeeValidate from 'vee-validate';  // Add this
        Vue.use(VeeValidate);  // Add this
3. Next, in /src/components/Skills.vue, modify the template:

        <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'min:5'" name="skill">
        <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        
4. Add a CSS ruleset for .alert:

        .alert {
            background: #fdf2ce;
            font-weight: bold;
            display: inline-block;
            padding: 5px;
            margin-top: -20px;
          }
          
5. it will still allow you to submit the form despite entering less than 5 characters.  

We can fix that by modifying the addSkill() method:

        addSkill() {
        this.$validator.validateAll().then((result) => {
          if (result) {
            this.skills.push({skill: this.skill});
            this.skill = '';
          } else {
            console.log('Not valid');
          }
        })
      }
      

        
 
 

