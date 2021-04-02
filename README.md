# SeaUrMusic

$ A website for everything music in Seattle link ( https://lucid-wozniak-ec7316.netlify.app/ )

$ To learn more about the author please visit the linkedin profile ( https://www.linkedin.com/in/jose-abreu/ )


# Build Setup

# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate

# SEO ( Search Engine Optimization) Learnings & Future Ideas

$ Lessons Learned: 

In simple terms, SEO is how search engines such as Google rank your website against other's. It’s also the practice of increasing both the quality and quantity of website traffic, as well as exposure to a website's brand in the search engine results. From what I have learned, the higher your SEO score, the more likely users will find your page through search engines. There are different techniques to increase an SEO score such as: Having only one H1 tag per page, Making reference or links to website that have high SEO score, adding proper title, description & keyword Metadata. There are many other SEO strategies but in general one should follow the guidlines below:


1) Crawl accessibility so engines can read your website
2) Compelling content that answers the searcher’s query
3) Keyword optimized to attract searchers & engines
4) Great user experience including a fast load speed and compelling UX
5) Share-worthy content that earns links, citations, and amplification
6) Title, URL, & description to draw high CTR in the rankings
7) Snippet/schema markup to stand out in SERPs

See https://moz.com/beginners-guide-to-seo for more reference on SEO best practices

$ Future Ideas to implement for SEO score increase

For this project, there are different ways we can improve the SEO score. Belo I will list a detailed list
of the ideas to implement.

1) Setting up default meta tags for all Nuxt.js pages.This would include a full descripttion of the page meta tag, title meta tag, links to high SEO score such as Ticketmaster.com.

2) Using the 'hid' unique identifeir for the meta tags on individual nuxt.js pages. The reason for this is beacuase when using the vue-meta package (https://vue-meta.nuxtjs.org/), 
it will create duplicate tags instead of replacing the original tag. Google can penalize the SEO score for having duplicate tags when it crawls your website. To fix this, implementing the unique hid property will avoid duplicate tags and improve SEO score.

3) Another idea to implement is to use the service of Sendgrid API to send users information of events through high SEO score pages.




