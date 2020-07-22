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
Here is a list of directives that you can use:

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


 
 

