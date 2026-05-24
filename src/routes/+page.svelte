<script>
    import { resolve } from "$app/paths";

    const pages = ["/home", "/view", "/viewmini"];
</script>

<h1>Root Page</h1>

<ul>
    {#each pages as path}
        <li>
            <!-- Using {} directly evaluates the JS function -->
            <a href={resolve(path)}>
                {resolve(path)}
            </a>
        </li>
    {/each}
</ul>
