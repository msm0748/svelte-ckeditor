<script>
	import { onMount } from 'svelte';

	let ClassicEditor;
	let editor;

	onMount(async () => {
		const module = await import('@ckeditor/ckeditor5-build-classic');
		ClassicEditor = module.default;

		ClassicEditor.create(document.querySelector('#editor'))
			.then((newEditor) => {
				editor = newEditor;
			})
			.catch((error) => {
				console.error(error);
			});
	});
</script>

<h1>Classic editor</h1>
<div id="editor">
	<p>This is some sample content.</p>
</div>

<button
	on:click={() => {
		console.log(editor.getData());
	}}>전송</button
>
