<template>
    <div id="app">

    	<div v-show="!file">

    		<drop @new-files="addFiles"></drop>

    		<file-list :files.sync="files" @show-form="showProcessForm" @remove-file="deleteFile"></file-list>

		</div>
		
		<div v-if="file">

			<process-form :file.sync="file" @close-form="closeProcessForm" @submit-upload="submitOne"></process-form>

		</div>

    </div>
</template>

<script>
    import Drop from './components/Drop'
    import FileList from './components/FileList'
    import ProcessForm from './components/ProcessForm'

    export default {
        name: 'App',
        data () {
        	return {
        		files: [],
        		file: null
        	}
        },

        components: {
            Drop,
            FileList,
            ProcessForm
        },

        methods: {
        	addFiles (files) {
        		return this.files.push( files )
        	},

        	deleteFile (file) {
        		let index = this.files.indexOf( file )

        		if ( index > -1 ) {

        			this.files.splice( index, 1 )

        		}

        		return
        	},

        	showProcessForm (file) {

        		this.file = file

        	},

        	closeProcessForm () {

        		this.file = null
        	},

        	submitOne (data) {
        		
        	}

        }

    }
</script>
