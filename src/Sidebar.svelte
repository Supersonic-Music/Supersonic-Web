<script>
    import Icon from '@iconify/svelte';
</script>

<div class="sidebar">
    <h1>Supersonic Web</h1>
    <div class="navlist">
        <a href="#" class="navbutton"><Icon icon="mdi:account" class="icon"/>Artists</a><br>
        <a href="#" class="navbutton"><Icon icon="mdi:album" class="icon"/>Albums</a>
    </div>
  </div>
  
<style>
    h1 {
        transition: all 0.3s ease-in-out;
        font-size: 2rem;
		font-weight: 700;
		line-height: 1;
		text-align: center;
		margin-bottom: 1em;
    }

    h1:hover {
        letter-spacing: -1.5px;
    }

    .sidebar {
        width: 200px;
        position: fixed;
        height: 100%;
        left: 0;
        top: 0;
        padding: 1rem;
        background-color: #292929;
        font-family: sans-serif;
        font-weight: bold;
        color: white;
    }

    :global(.icon) {
        height: 1.8rem;
        vertical-align: middle;
        position: relative;
        top: -2.5px;
        margin-right: 5px;
    }

    .navlist {
        padding: 0;
        margin: 0;
    }

    .navbutton {
        display: block;
        color: white;
        text-decoration: none;
        font-size: 1.5rem;
        transition: all 0.3s ease-in-out;
        border-radius: 10px;
        padding: 10px 15px;
    }

    .navbutton:hover {
        color: white;
        background-color: #1c1c1c;
        letter-spacing: 2px;
    }  
</style>