<script>
  export let articles = [];
</script>

<section class="more-to-discover">
  <div class="container">
    <h2 class="section-title">More to Discover</h2>
    <div class="articles-grid">
      {#each articles as article (article.id)}
        <article class="article-card">
          {#if article.image}
            <a href={article.href} class="article-image-link">
              <div class="article-image">
                <img src={article.image} alt={article.title} />
                {#if article.label}
                  <span class="label">{article.label}</span>
                {/if}
              </div>
            </a>
          {/if}
          <div class="article-content">
            {#if article.category}
              <span class="category">{article.category}</span>
            {/if}
            <h3 class="article-title">{article.title}</h3>
            {#if article.description}
              <p class="article-description">{article.description}</p>
            {/if}
            {#if article.author}
              <span class="article-meta">By {article.author}</span>
            {/if}
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<style lang="scss">
  @import '../styles/mixins';

  .more-to-discover {
    padding: 2.5rem 1.5rem;
    margin-top: 3rem;
    border-top: 3px double #52b788;
    border-bottom: 3px double #52b788;
    background: linear-gradient(135deg, #3d6e4f 0%, #2d5a3d 100%);
    background-color: #2d5a3d;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0;
  }

  .section-title {
    font-size: 1.8rem;
    font-weight: 400;
    margin-bottom: 1.5rem;
    color: #f5f1e8;
    font-family: 'Georgia', serif;
    letter-spacing: 0.1em;
    text-align: center;
    text-transform: uppercase;
    border-bottom: 2px solid #81c784;
    padding-bottom: 1rem;
    font-style: italic;
  }

  .articles-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;

    @media (min-width: 768px) {
      grid-template-columns: repeat(3, 1fr);
    }

    @media (max-width: 768px) {
      grid-template-columns: repeat(2, 1fr);
    }

    @media (max-width: 480px) {
      grid-template-columns: 1fr;
    }
  }

  .article-image-link {
    display: block;
    text-decoration: none;
  }

  .article-card {
    display: flex;
    flex-direction: column;
    background-color: #f5f1e8;
    border: 1px solid #9f9577;
    box-shadow: 
      0 2px 4px rgba(52, 168, 83, 0.2),
      inset 0 1px 0 rgba(255, 255, 255, 0.5);
    transition: box-shadow 0.3s ease, transform 0.3s ease;
    position: relative;
    
    &::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-image: 
        repeating-linear-gradient(
          0deg,
          rgba(52, 168, 83, 0.03) 0px,
          rgba(52, 168, 83, 0.03) 1px,
          transparent 1px,
          transparent 2px
        );
      pointer-events: none;
    }

    &:hover {
      box-shadow: 
        0 6px 12px rgba(52, 168, 83, 0.3),
        inset 0 1px 0 rgba(255, 255, 255, 0.5);
      transform: translateY(-3px);
    }
  }

  .article-image {
    position: relative;
    width: 100%;
    padding-bottom: 66.67%;
    overflow: hidden;
    background-color: #8f9b7d;
    border-bottom: 2px solid #34a853;

    img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      filter: sepia(0.2) contrast(1.05) saturate(0.8);
    }
  }

  .label {
    position: absolute;
    top: 0.75rem;
    right: 0.75rem;
    background-color: rgba(52, 168, 83, 0.85);
    color: #f5f1e8;
    font-size: 0.7rem;
    font-weight: 600;
    padding: 0.4rem 0.7rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    border: 1px solid #81c784;
    font-family: 'Georgia', serif;
  }

  .article-content {
    padding: 1.25rem;
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }

  .category {
    font-size: 0.7rem;
    font-weight: 600;
    text-transform: uppercase;
    color: #34a853;
    letter-spacing: 0.15em;
    margin-bottom: 0.75rem;
    font-family: 'Georgia', serif;
  }

  .article-title {
    font-size: 0.95rem;
    font-weight: 600;
    line-height: 1.3;
    color: #1f3a1f;
    margin-bottom: 0.5rem;
    font-family: 'Georgia', serif;
    letter-spacing: 0.02em;

    &:hover {
      color: #34a853;
    }
  }

  .article-description {
    font-size: 0.85rem;
    line-height: 1.5;
    color: #5a5c52;
    margin-bottom: auto;
    margin-top: 0.4rem;
    font-family: 'Georgia', serif;
  }

  .article-meta {
    font-size: 0.75rem;
    color: #7a8370;
    margin-top: 0.5rem;
    font-weight: 500;
    font-style: italic;
    font-family: 'Georgia', serif;
  }
</style>
