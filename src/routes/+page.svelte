<script>
    import { resolve } from "$app/paths";

    const pages = ["/home", "/view", "/viewmini"];
</script>

<h1>Root Page</h1>

<ul>
    {#each pages as path}
        <li>
            <!-- Using {} directly evaluates the JS function -->
            <a href={resolve(path)} style="font-size: large; font-weight: 800;">
                {resolve(path)}
            </a>
        </li>
    {/each}
</ul>
