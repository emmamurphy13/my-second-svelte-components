<!--
@component
This is your page!
-->
<script>
  // Import all the news furniture components
  import ArticleHeader from '$lib/components/ArticleHeader.svelte';
  import ArticleBody from '$lib/components/ArticleBody.svelte';
  import Image from '$lib/components/Image.svelte';
  import RelatedLinks from '$lib/components/RelatedLinks.svelte';
  import MoreToDiscover from '$lib/components/MoreToDiscover.svelte';
  import FunFactPanel from '$lib/components/FunFactPanel.svelte';
  import AuthorBio from '$lib/components/AuthorBio.svelte';


  // Article metadata
  let headline = 'Emma Murphy and her spreadsheets.';
  let byline = 'NYCity News Service';
  let pubDate = '2026-01-31';

  // Author information
  const authorInfo = {
    name: 'Ben Welsh',
    photo: '/welsh.avif',
    bio: 'Ben Welsh is the editor of the News Applications Team at Reuters, where he leads a group of journalist-programmers who build data-driven investigations and interactive graphics.',
    email: '',
    portfolio: 'https://www.reuters.com/authors/ben-welsh/',
    linkedin: '',
    note: 'Professor Welsh generously wrote bios about all of his students, including Emma, for the NYC News Service.'
  };

  // Related stories
  const relatedStories = [
    { headline: 'How America\'s top news organizations escape rigid publishing systems to design beautiful data-driven stories on deadline.', href: 'https://palewi.re/docs/coding-the-news/' },
    { headline: 'How to install, configure and use Visual Studio Code, GitHub and Copilot', href: 'https://palewi.re/docs/coding-the-news/scripts/week-1/' },
    { headline: "How to publish a website with Node.JS and GitHub Actions", href:"https://palewi.re/docs/coding-the-news/scripts/week-2/"},
  ];

  // More to discover articles
  const moreToDiscoverArticles = [
    {
      id: 1,
      image: '/niemen.webp',
      title: 'These Newsrooms Are Trying to Boost Trust Through Transparency',
      category: 'Media',
      description: 'Across the world, newsrooms are experimenting with radical transparency—from ethics boxes to detailed methodology sharing—to rebuild trust with skeptical audiences.',
      author: 'Gretel Kahn',
      label: null,
      href: 'https://www.niemanlab.org/2025/05/these-newsrooms-are-trying-to-boost-trust-through-transparency-is-it-working/'
    },
    {
      id: 2,
      image: '/reporter.webp',
      title: 'New Reporter on Data Journalism Team',
      category: 'Career',
      description: 'Matt Zdun joins The New York Times Data Journalism team to cover the federal government and political campaigns, bringing experience from The Houston Chronicle.',
      author: 'Jeremy Singer-Vine',
      label: null,
      href: 'https://www.nytco.com/press/new-reporter-on-data-journalism-team/'
    },
    {
      id: 3,
      image: '/front.webp',
      title: 'FRONTLINE and Newmark J-School Announce 2026 Tow Journalism Fellow',
      category: 'Education',
      description: 'Leo Miranda, a Newmark J-School graduate specializing in data journalism and local accountability reporting, has been selected as a 2026 Tow Journalism Fellow.',
      author: 'FRONTLINE',
      label: null,
      href: 'https://www.pbs.org/wgbh/frontline/announcement/frontline-and-newmark-j-school-announce-2026-tow-journalism-fellow/'
    }
  ];

  // Fun facts for the side panel
  const funFacts = [
    {
      text: 'Emma desperately wants a cat',
      
    },
    {
      text: "Emma's favorite book is \"My Brilliant Friend\".",
      
    },
    {
      text: 'Emma grew up in Syracuse, NY.',
      
    },
    {
      text: 'Emma has an obsession with the Statue of liberty and Ellis Island.',
      
    },
    
  ];

</script>

<!-- This sets the page title in the browser tab -->
<svelte:head>
  <title>{headline} | NYCity News Service</title>
  <meta name="description" content="At the Craig Newmark Graduate School of Journalism at the City University of New York, change is in our DNA. That comes of being born in 2006, as the digital revolution was transforming our profession in ways none of us could have imagined." />
</svelte:head>

<!-- Your page content goes here -->
<div class="container">
  
  <!-- Article Header: Headline, byline, and publication date -->
  <ArticleHeader
    {headline}
    {byline}
    {pubDate}
  />

  <!-- Lead Image: Animated gif of students at the journalism school -->
  <Image
    src="/sheets.webp"
    alt="A platform Emma Murphy uses frequently in her work."
    caption="A platform Emma Murphy uses frequently in her work."
    credit="Google"
  />

  <!-- Author Bio: Photo, description, and links -->
  <AuthorBio author={authorInfo} />

  <!-- Article Body: The main story text with proper typography -->
  <ArticleBody>
    <p>
      Emma Murphy is a student at the Craig Newmark Graduate School of Journalism at CUNY, aspiring to become a data journalist. With a keen interest in using spreadsheets and data analysis tools to uncover hidden stories, Emma represents a new generation of journalists who are equipped with both traditional reporting skills and modern technical expertise.
    </p>

    <p>
      She is passionate about using data to uncover stories that matter and is excited to be part of a community of journalists who are dedicated to making a positive impact in the world. Her work focuses on finding patterns in large datasets that reveal insights about society, economics, and policy.
    </p>

    <p>
      Transparency is under threat in the news industry. Murphy deeply believes in supporting reporting that aims to be objective. She advocates for newsrooms to show their work, explain methodologies and sources so audiences can understand how journalists reached their conclusions. This approach builds trust through clarity and accountability.
    </p>

    <p>
      In her own reporting, Murphy most enjoys covering the economics of her favorite place: New York City. She has explored topics ranging from housing policy to public transit infrastructure, using spreadsheet analysis to give context and depth to her stories. Her work exemplifies the power of combining traditional journalism with data-driven investigation.
    </p>

    <p>
      As a student at the Newmark J-School, Murphy has learned that data journalism is not just about numbers and charts—it's about storytelling. Every dataset has a human story waiting to be discovered, and her goal is to use her skills to tell those stories in ways that inform and engage audiences.
    </p>
  </ArticleBody>

  <!-- Article Body with Sidebar Layout -->
  <div class="article-with-sidebar">
    <div class="article-main">
      <!-- Related Stories: Links to other articles -->
      <RelatedLinks
        title="Related Stories"
        links={relatedStories}
      />
    </div>
    
    <!-- Fun Fact Panel: Interesting side information -->
    <aside class="article-sidebar">
      <FunFactPanel facts={funFacts} />
    </aside>
  </div>

  <!-- More to Discover: Additional reading suggestions -->
  <MoreToDiscover articles={moreToDiscoverArticles} />

</div>

<style>
  /* Styles here only apply to this page */
  .container {
    padding: var(--spacing-lg) var(--spacing-md);
    position: relative;
  }

  .article-with-sidebar {
    display: grid;
    grid-template-columns: 1fr;
    position: relative;
  }

  .article-main {
    min-width: 0;
    max-width: 800px;
  }

  .article-sidebar {
    position: fixed;
    right: 2rem;
    top: 200px;
    width: 280px;
  }

  /* Tablet: Stack vertically */
  @media (max-width: 1200px) {
    .article-sidebar {
      position: static;
      width: auto;
      margin-top: 2rem;
    }

    .article-with-sidebar {
      grid-template-columns: 1fr;
    }
  }

  /* Mobile: Stack vertically */
  @media (max-width: 768px) {
    .article-sidebar {
      position: static;
      width: auto;
    }
  }
</style>