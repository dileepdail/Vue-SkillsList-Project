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
      
###### Vue Animations

1. Add these 3 line

        <transition name="alert-in">
                <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>
        
2. Add in CSS section

        .alert-in-enter-active {
          animation: bounce-in .5s;
        }
        .alert-in-leave-active {
          animation: bounce-in .5s reverse;
        }
        @keyframes bounce-in {
          0% {
            transform: scale(0);
          }
          50% {
            transform: scale(1.5);
          }
          100% {
            transform: scale(1);
          }
        }
        
###### The transition classes that you have at your disposal are:

* v-enter
* v-enter-active
* v-enter-to
* v-leave
* v-leave-active
* v-leave-to

*Animate.css is a popular animation library that works great with UI animations.*

        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
                <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>
        
Add in CSS section  
        
        <style scoped>
        @import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
        
Animating Lists

        <ul>
          <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
            <li v-for="(data, index) in skills" :key='index'>{{data.skill}}</li>
          </transition-group>
        </ul>
        
## Vue Router

1. Add vue-router in your project
        
                npm add vue-router
        
2. Create a /src/router.js

        import Vue from 'vue'
        import Router from 'vue-router'
        import Skills from './components/Skills.vue'
        import About from './components/About.vue'

        Vue.use(Router)

        export default new Router({
          routes: [
            {
              path: '/',
              name: 'skills',
              component: Skills
            },
            {
              path: '/about',
              name: 'about',
              component: About
            }
          ]
        })
        
 3. Create About.vue file
 
        <template>
          <div class="about">
            <h1>This is an about page</h1>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna ali...</p>
          </div>
        </template>
        
4. In /src/main.js and add the following:

        import router from './router'

        new Vue({
          router,               // Add this line
          render: h => h(App)
        }).$mount('#app')
        
5. /src/App.vue file and modify the <template> section as shown:
        
        <template>
          <div id="app">
              <nav>
                <router-link to="/">Home</router-link>
                <router-link to="/about">About</router-link>
              </nav>
            <router-view/>
          </div>
        </template>
      

        
 
 

