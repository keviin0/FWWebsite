<script>
    import '../styles.css';
    import { onMount } from 'svelte';

    var message = "";
    onMount(async () => {
        try {
            const userLang = navigator.language || navigator.userLanguage;
            const response = await fetch('./messages.json');
            const messages = await response.json();
            message = messages[userLang.split('-')[0]] || messages['en']; // Fallback to English if the language is not found
        } catch (error) {
            console.error('Error fetching the messages:', error);
            message = 'Error loading message.';
        }
    });
</script>

<div class="wills-will">
    <div class="wills-message">
        {message}
    </div>
</div>

<style>
    .wills-will {
        height: 100vh;
        display:flex;
        justify-content: center;
        align-items: center;
        background-color: black;
        color: #fffee9;
    }

    .wills-message {
        width: 60vw;
        font-family: "Fira Code", monospace;
        font-size: clamp(1rem, 1.5vw, 3rem);
    }
</style>