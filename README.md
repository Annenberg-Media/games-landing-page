<h3>What this does:</h3>

- index.html controls what you see on https://annenberg-media.github.io/games-landing-page/ (deployed using Github Pages), and subsequently on https://www.uscannenbergmedia.com/games/ (fetched from the GH Pages version using some magical JS in the HTML box on /games page in Arc PageBuilder)  
<br/>
<h3>Add another card:</h3>

- Uncomment the `<div class="p-4 md:w-1/3">` element entirely, should add another item to the group  
<br/>

<h3>Points to note:</h3>

- if you include any `<script>` in the body (and preferably in the body because the fetch happens from the body elements), you have to add in those `<script>` elements to the Arc HTML box as well (see how Tailwind CSS and Bootstrap.bundle.min.js are included separately in the Arc HTML box, besides also being in index.html)
- `<link href>` are fine, they don't need to be added again (see how Bootstrap.min.css is not included in the Arc HTML box)
- the reason `<script>` need to be added, is because they are not executed when fetched (protection measure), and dynamically running them on fetch (I have tried this), leads to a broken UX with weird styling and behaviour as the different `<script>` load one by one. Not ideal.
- If you are using Bootstrap modals, ensure `data-bs-backdrop="false"` is set on the windowModal element (see index.html), this prevents the dark background from loading (an extra bg is loaded for Arc's version by the Bootstrap JS script which prevents user input due to very high z-index, setting the bs-backdrop to false allows user input by disabling the dark background)