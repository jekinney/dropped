<template>
	<table v-if="files && files.length > 0" class="invisible table admin-table">
		<thead>
			<tr>
				<th scope="col">File Name</th>
      			<th scope="col">Size</th>
      			<th scope="col">Upload Date</th>
      			<th scope="col">Type</th>
      			<th scope="col"></th>
			</tr>
		</thead>
		<tbody>
			<tr v-for="file in files">
				<td>{{ file.name }}</td>
				<td>{{ file.size }}</td>
				<td>{{ Date() }}</td>
				<td>{{ file.type }}</td>
				<td>
					<button type="button" @click="processForm(file)">Process</button>
					<button type="button" @click="removeFile(file)">Delete</button>
				</td>
			</tr>
		</tbody>
	</table>
</template>

<script>
	export default {
		name: 'file-list',

		props: ['files'],

		methods: {
			processForm (file) {
				this.$emit('show-form', file)
			},
			removeFile (file) {
				this.$emit('remove-file', file)
			}
		}
	}
</script>