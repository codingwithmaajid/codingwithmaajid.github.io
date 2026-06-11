<svelte:head>
  <title>Tech Stack — Abdul Maajid</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
  <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=Inter:wght@400&display=swap" rel="stylesheet" />
</svelte:head>

<script>
  const CDN = 'https://cdn.jsdelivr.net/npm/simple-icons@latest/icons';

  const stack = [
    {
      category: 'Languages',
      items: [
        { name: 'Python',  slug: 'python',     color: '#3776AB' },
        { name: 'Rust',    slug: 'rust',        color: '#CE422B' },
        { name: 'C++',     slug: 'cplusplus',   color: '#00599C' },
        { name: 'C',       slug: 'c',           color: '#A8B9CC' },
      ],
    },
    {
      category: 'Infrastructure',
      items: [
        { name: 'Linux',   slug: 'linux',       color: '#FCC624' },
        { name: 'Docker',  slug: 'docker',      color: '#2496ED' },
        { name: 'Git',     slug: 'git',         color: '#F05032' },
        { name: 'GitHub',  slug: 'github',      color: '#ffffff' },
      ],
    },
  ];

  let hovered = null;
</script>

<main>
  <a class="back" href="/">← back</a>
  <h1>Tech Stack</h1>
  <p class="subtitle">Tools and languages I use and explore.</p>

  {#each stack as group}
    <section>
      <p class="group-label">{group.category}</p>
      <div class="grid">
        {#each group.items as item}
          <div
            class="item"
            on:mouseenter={() => hovered = item.slug}
            on:mouseleave={() => hovered = null}
          >
            <div class="logo">
              <img
                src="{CDN}/{item.slug}.svg"
                alt={item.name}
                width="28"
                height="28"
                style="filter: {hovered === item.slug ? 'brightness(0) invert(1)' : 'brightness(0) invert(0.5)'};"
                loading="lazy"
              />
            </div>
            <span class="item-name" style="color: {hovered === item.slug ? item.color : '#6b6660'}">
              {item.name}
            </span>
          </div>
        {/each}
      </div>
    </section>
  {/each}
</main>

<style>
  :global(html, body) {
    margin: 0;
    padding: 0;
    background: #080808;
  }

  main {
    max-width: 680px;
    margin: 0 auto;
    padding: 4rem 2rem 6rem;
    font-family: 'Inter', sans-serif;
  }

  .back {
    font-size: 0.8125rem;
    color: #6b6660;
    text-decoration: none;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    display: inline-block;
    margin-bottom: 3rem;
  }

  .back:hover {
    color: #c9b99a;
  }

  h1 {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(2rem, 6vw, 3rem);
    font-weight: 400;
    color: #f0ede8;
    line-height: 1.05;
    letter-spacing: -0.02em;
    margin: 0 0 0.75rem;
  }

  .subtitle {
    font-size: 0.9375rem;
    color: #6b6660;
    margin: 0 0 3.5rem;
  }

  section {
    margin-bottom: 3rem;
  }

  .group-label {
    font-size: 0.75rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: #4a4640;
    margin: 0 0 1.25rem;
  }

  .grid {
    display: flex;
    flex-wrap: wrap;
    gap: 0;
  }

  .item {
    width: 100px;
    padding: 1.5rem 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.75rem;
    cursor: default;
    transition: background 0.2s;
    border-radius: 4px;
  }

  .item:hover {
    background: #111010;
  }

  .logo {
    width: 28px;
    height: 28px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .logo img {
    width: 28px;
    height: 28px;
    transition: filter 0.2s;
  }

  .item-name {
    font-size: 0.8125rem;
    letter-spacing: 0.01em;
    transition: color 0.2s;
  }

  @media (max-width: 480px) {
    main {
      padding: 2.5rem 1.25rem 4rem;
    }

    .item {
      width: 80px;
    }
  }
</style>