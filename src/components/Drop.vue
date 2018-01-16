<template>
    <div>

        <div class="drop-area"  @dragover.prevent @drop.prevent="getDropedFiles" @click="findFile">

            <p class="drop-area-text">Drag one or more files here or click to add a file.</p>

        </div>

        <input type="file" id="fileinput" class="invisable" @change.prevent="getFile">

    </div>
</template>

<script>
    export default {
        name: 'Drop',

        methods: {

            findFile () {

                let input = document.getElementById('fileinput')

                let event = document.createEvent('MouseEvents')

                event.initEvent('click', false, true)

                input.dispatchEvent(event)

            },

            getFile (e) {

                var uploads = e.target.files || e.dataTransfer.files;

                if ( uploads.length ) {

                    this.$emit('new-files', uploads[0] )
                
                }


                return;

            },

            getDropedFiles (e) {

                e.preventDefault()

                let upload = e.dataTransfer;

                if ( upload.items ) {

                    for (let i=0; i < upload.items.length; i++) {

                        if ( upload.items[i].kind == "file" ) {

                             this.$emit('new-files', upload.items[i].getAsFile() )

                        }

                    }
                
                } else {

                    for ( let i=0; i < upload.files.length; i++ ) {

                         this.$emit('new-files', upload.files[i] )

                    }

                } 

            },

        }
    }
</script>

<style scoped>
    .drop-area {
        height: 400px;
        width: 100%;
        position: relative;
        border: .1em solid grey;
        border-radius: .5em;
    }

    .drop-area:hover {
        border-color: black;
        cursor: pointer;
        color: black;
    }

    .drop-area-text {
        color: grey;
        font-size: 1.5em;
        font-weight: bold;
        position: absolute;
        top: 35%;
        left: 35%;
    }
    
    .drop-area:hover > p {
        color: black;
    }

    .invisable {
        display: none;
    }
</style>
