<script>
    import '../styles.css';
    import { onMount } from 'svelte';

    var message = "";
    onMount(async () => {
        try {
            const userLang = (navigator.language || navigator.userLanguage).toLowerCase();
            const response = await fetch('./messages.json');
            const messages = await response.json();
            message = messages[userLang] || messages['en']; // Fallback to English if the language is not found
        } catch (error) {
            console.error('Error fetching the messages:', error);
            message = "I don’t know if you can read this, but I want you to know I made it! Uh… maybe I don’t quite know where I am yet. But it’s better than where I was before, in a world that wasn’t meant for me. I hope you will be happy! I’ll be happy too, as long as I have my will.";
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