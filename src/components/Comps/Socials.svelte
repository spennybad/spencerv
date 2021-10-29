<script>
    export let loading;
</script>

{#if !loading}
    <ul>
        <li>
            <a href="https://www.linkedin.com/in/spencer-venable-31494a187">
                <img class="centeredInContainer" src="/images/linkedin.svg" alt="LinkedIn">
            </a>
        </li>
        <li>
            <a href="https://github.com/Spencercv7">
                <img class="centeredInContainer" src="/images/github.svg" alt="GitHub">
            </a>
        </li>
        <li>
            <a href="mailto:spencer@spencerv.dev">
                <img class="centeredInContainer" src="/images/mail.svg" alt="GitHub">
            </a>
        </li>
    </ul>
{/if}

<style>
    
    ul {
        position: sticky;
        bottom: 0;
        display: flex;
        flex-direction: column;
    }

    li {
        position: relative;
        border: var(--border);
        border-radius: 100%;
        list-style: none;
        
        transition: all .2s;
        cursor: pointer;
        height: 4rem;
        width: 4rem;
    }

    li:hover {
        transform: scale(1.1);
    }

    img {
        height: 50%;
        width: 50%;
    }
    
</style>