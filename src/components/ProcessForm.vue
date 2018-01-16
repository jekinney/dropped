<template>
	<form>
		
		<button type="button" @click="cancel" >Cancel </button>

		<table class="invisible table admin-table">
			<thead>
				<tr>
					<th scope="col">File Name</th>
	      			<th scope="col">Size</th>
	      			<th scope="col">Upload Date</th>
	      			<th scope="col">Type</th>
				</tr>
			</thead>
			<tbody>
				<tr>
					<td>{{ file.name }}</td>
					<td>{{ file.size }}</td>
					<td>{{ Date() }}</td>
					<td>{{ file.type }}</td>
				</tr>
			</tbody>
		</table>

		<div class="row file-params">
			
		  	<div class="col-12 col-sm-6 col-md-6  col-lg-3 file-param-box">
		    	<label>Division</label>
		    	<select class="custom-select">
		      		<option value="orv">ORV</option>
		      		<option value="option 2">Option 2</option>
		    	</select>
		  	</div>

		  	<div class="col-12 col-sm-6 col-md-6  col-lg-3 file-param-box">
		    	<label>Model Year</label>
		    	<select class="custom-select">
		      		<option value="2018">2018</option>
		      		<option value="2017">2017</option>
		    	</select>
		  	</div>

		  	<div class="col-12 col-sm-6 col-md-6  col-lg-3 file-param-box">
		    	<label>Country</label>
		    	<select class="custom-select multiselect" name="country[]" multiple="multiple" placeholder="Choose Countries">
		      		<option value="1">US</option>
		      		<option value="2">France</option>
		      		<option value="3">Mexico</option>
		   		</select>
		  	</div>

		  	<div class="col-12 col-sm-6 col-md-6  col-lg-3 file-param-box">
		    	<label>Launch Permissions</label>
		    	<select class="custom-select multiselect" name="permissions[]" multiple="multiple" placeholder="Choose Permissions">
		      		<option value="1">2017 ORV Launch</option>
		      		<option value="2">2018 Ranger 1000</option>
		    	</select>
		  	</div>

		  	<div class="col-12"></div>

		  	<div class="col-12 col-sm-6 col-md-6  col-lg-3 file-param-box">
		    	<label>Language</label>
		    	<select class="custom-select multiselect" name="language[]" multiple="multiple" placeholder="Choose Languages">
		      		<option value="1">English</option>
		      		<option value="2">Spanish</option>
		      		<option value="3">Other</option>
		    	</select>
		  	</div>

		  	<div class="col-12 col-sm-6 col-md-6  col-lg-3 file-param-box">
			    <label>Location</label>
			    <select class="custom-select multiselect" name="location[]" multiple="multiple" placeholder="Choose Locations">
			      	<option value="1">Snow</option>
			      	<option value="2">Desert</option>
			      	<option value="3">Studio</option>
			      	<option value="4">Woods</option>
			    </select>
		  	</div>

		  	<div class="col-12 col-sm-6 col-md-6  col-lg-3 file-param-box">
			    <label>Content Type</label>
			    <select class="custom-select multiselect" name="contenttype[]" multiple="multiple" placeholder="Choose Content Type">
			      	<option value="1">CGI</option>
			      	<option value="2">Print Ad</option>
			      	<option value="3">Video</option>
			    </select>
		  	</div>

		  	<div class="col-12 col-sm-6 col-md-6  col-lg-3 file-param-box">
		    	<label>File Use</label>
		    	<select class="custom-select multiselect" name="fileuse[]" multiple="multiple" placeholder="Choose File Use">
		      		<option value="1">Print</option>
		      		<option value="2">Web</option>
		    	</select>
		  	</div>
			
			<div class="form-group">
	        	<button class="btn btn-blue">Process</button>
	      	</div>

		</div>

	</form>
</template>

<script>
	export default {
		name: 'process-form',
		props: ['file'],
		data () {
			return {
				errors: []
			}
		},
		mounted () {
			this.setUpPage()
		},
		methods: {
			setUpPage () {
				// get all the seed data for select inputs
			},
			cancel () {
				this.$emit('close-form')
			},
			submitForm () {
				this.$emit('submit-upload', {
					file: this.file, 
					form: this.form
				})
			}
		}
	}
</script>