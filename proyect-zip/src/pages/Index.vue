<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-vertical.svg"
      style="width: 200px; height: 200px"
    >
  </q-page>
</template>

<script>
import JsZip from 'jszip' 
import  saveAs  from 'file-saver';
    export default {
      name: 'HelloWorld',
      created() {
        var zip = new JsZip();
        zip.file("Hello.txt", "Hello World\n");
        var img = zip.folder("images");
        //img.file("smile.gif", imgData, {base64: true});
        zip.generateAsync({type:"blob"})
        .then(function(content) {
            // see FileSaver.js
            saveAs(content, "example.zip");
        });
          // **ReferenceError: JSZip is not defined**
      },
      data () {
        return {
          msg: 'Welcome to Your Vue.js App'
        }
      }
    }
</script>
