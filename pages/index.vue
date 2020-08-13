<template>
  <div class="container">
    <VueTerminal
      :intro="welcomeMessage"
      console-sign="->"
      allow-arbitrary
      :full-screen="true"
      :commands="commands"
      @command="onCliCommand">

    </VueTerminal>

  </div>
</template>

<script>
  import VueTerminal from '@/components/VueTerminal';

  export default {
    components: {
      VueTerminal
    },
    data() {
      return {
        welcomeMessage:
          "Welcome to my blog 🥳 <br>" +
          "I'm Miqdad Farcha, a backend developer <br>" +
          "Please type 'help' to know me more 💬",
        commands: [
          {
            name: 'ls',
            method: function (cmd) {
              cmd.out = 'Hello world!'
              return cmd
            },
            help: 'A demo command.'
          }
        ]
      }
    },
    mounted() {
      this.commands.push({
        name: 'lsa',
        method: function (cmd) {
          cmd.out = 'Hello world!'
          return cmd
        },
        help: 'A demo command.'
      })
    },
    methods: {
      onCliCommand(data, resolve, reject) {
        
      },
      printHorizontal(data){
        let result = '';
        data.forEach(d => {
          result += `${d} &nbsp;`
        })
        return result;
      }
    }
  }
</script>

<style>
  .container {
    height: 100%;
  }
</style>
