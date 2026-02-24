<script>
  export let author = {
    name: '',
    photo: '',
    bio: '',
    email: '',
    portfolio: '',
    linkedin: '',
    note: ''
  };
</script>

<div class="author-bio">
  <div class="author-photo">
    <img src={author.photo} alt={author.name} />
  </div>
  <div class="author-info">
    <h3 class="author-name">{author.name}</h3>
    <p class="author-description">{author.bio}</p>
    {#if author.note}
      <p class="author-note">{author.note}</p>
    {/if}
    <div class="author-links">
      {#if author.email}
        <a href="mailto:{author.email}" class="author-link">Email</a>
      {/if}
      {#if author.portfolio}
        <a href={author.portfolio} target="_blank" rel="noopener noreferrer" class="author-link">Portfolio</a>
      {/if}
      {#if author.linkedin}
        <a href={author.linkedin} target="_blank" rel="noopener noreferrer" class="author-link">LinkedIn</a>
      {/if}
    </div>
  </div>
</div>

<style lang="scss">
  @use '../styles/mixins' as *;

  .author-bio {
    display: flex;
    gap: 0.5rem;
    padding: 0.75rem 0;
    margin: 0 0 1rem 0;
    background: transparent;
    border: none;
    border-top: 1px solid #e8dfd0;
    border-bottom: 1px solid #e8dfd0;
    
    @media (max-width: 768px) {
      flex-direction: row;
      align-items: flex-start;
    }
  }

  .author-photo {
    flex-shrink: 0;
    
    img {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      object-fit: cover;
      border: 1px solid #34a853;
    }
  }

  .author-info {
    flex: 1;
  }

  .author-name {
    font-family: Georgia, serif;
    font-size: 0.85rem;
    font-weight: 600;
    color: #2d8e47;
    margin: 0 0 0.25rem 0;
  }

  .author-description {
    font-family: Georgia, serif;
    font-size: 0.75rem;
    line-height: 1.4;
    color: #3d3d3d;
    margin: 0 0 0.25rem 0;
  }

  .author-note {
    font-family: Georgia, serif;
    font-size: 0.7rem;
    line-height: 1.3;
    color: #666;
    font-style: italic;
    margin: 0 0 0.25rem 0;
  }

  .author-links {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    
    @media (max-width: 768px) {
      justify-content: flex-start;
    }
  }

  .author-link {
    font-family: Georgia, serif;
    font-size: 0.75rem;
    color: #34a853;
    text-decoration: none;
    padding: 0.1rem 0;
    border-bottom: 1px solid transparent;
    transition: all 0.2s ease;
    
    &:hover {
      color: #2d8e47;
      border-bottom-color: #2d8e47;
    }
  }
</style>
