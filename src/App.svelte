<script lang="ts">
	import {S3Client, ListObjectsCommand} from '@aws-sdk/client-s3';
	let accountName = '';
	let accessKeyId = '';
	let secretAccessKey = '';

	async function handleSubmit() {
		const client = new S3Client({ 
			region: 'ap-northeast-2',
			credentials: {
				accessKeyId: accessKeyId,
				secretAccessKey: secretAccessKey,
			}
		});


		const command = new ListObjectsCommand({ Delimiter: "/", Bucket: 'bdbdbdleebucket' })
		const response = await client.send(command);
		console.log(response);
	}
	
</script>

<main>
	<div><label for="account-name">Account Name: </label><input type="text" id="account-name" bind:value={accountName}/></div>
	<div><label for="access-key-id">Access Key Id: </label><input type="text" id="access-key-id" bind:value={accessKeyId}/></div>	
	<div><label for="secret-access-key">Secret Access Key: </label><input type="password" id="secret-access-key" bind:value={secretAccessKey}/></div>
	<button on:click={handleSubmit}>connect</button>
</main>

<style>
</style>