---
title: "Subatomica: A definitive guide to subatomic particles"
datePublished: Tue Aug 15 2023 14:04:00 GMT+0000 (Coordinated Universal Time)
cuid: cllcdk28g000i09mre6c29b1f
slug: subatomica-a-definitive-guide-to-subatomic-particles
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692109383221/e8a5745d-f571-45d6-806a-1b0f1d83a8fa.jpeg
tags: grafbasehackathon, grafbase

---

I had a few days free after Hashnode announced Hackathon on using Grafbase. So I built a blog based portal on information regarding subatomic particles called Subatomica using Next.js, Grafbase and Contentful CMS. This is my official entry to [Hashnode Grafbase Hackathon](https://hashnode.com/hackathons/grafbase?source=hackathon-feed-widget).

## **What is Subatomica?**

Most of us have heard about Protons, Electrons, And Neutrons. Have you ever wondered what these particles are themselves made up of?  
Welcome To Subatomica:  
Here we step into the captivating realm of subatomic elementary particles, where Electrons, Quarks, Neutrinos, and their elusive cousins come to life through captivating narratives and insightful exploration.

[Subatomica](https://subatomica.vercel.app/) is not just a blog related to subatomic particles but also a Next.js starter template to set up your own blog using Next.js, Grafbase and Contentful CMS.

## **Why I created this project?**

I recently watched Big Bang Theory and was interested in learning about subatomic particles in more detail. There might be a target audience who would be interested in the same topic. So I decided to build a project on this topic since it seemed unique and pretty interesting. Besides, this would also allow me to learn more about Grafbase and sharpen my front-end development skills.

## **What is Grafbase?**

[Grafbase](https://grafbase.com/) is the easiest way to build and deploy your own GraphQL API to the edge with full end-to-end type safety. Integrate any data source using resolvers and connectors, configure edge caching, set auth and permission rules, enable serverless search, and more with Grafbase. With Grafbase, you can also work locally using the Grafbase CLI. Each Git branch includes a dedicated preview deployment for easy testing and collaboration.

## **What is the tech stack used?**  

Subatomica is built using below technologies:-

1. **Next.js** as a frontend framework to build Blog UI.
    

1. **Contentful** CMS as a data source for blog posts.
    
2. **Grafbase** as edge gateway to unify data from Contentful and serve data to frontend framework using GraphQL queries.
    
3. **GraphQL** as the query language for APIs and fulfilling those queries with your contentful data.
    
4. **Tailwind CSS** for styling the pages and responsive website design
    

## **Challenges faced while building the project**

The first hurdle was choosing a good topic for the hackathon. I used Contentful for the first time so learning about how to use the GraphQL endpoint of Contentful was a bit of a challenge. Using Graphbase Edge gateway for Contentful was easy, thanks to a couple of articles written on the topic.

## **Usage of Grafbase in my project**

In this project, I have set up blog posts with Grafbase and Contentful. I created a content model, connected Grafbase, and wrote queries for our blog post data.

The Grafbase [Edge Gateway](https://grafbase.com/edge-gateway) allows us to unify data at the edge by glueing GraphQL and non-GraphQL services together.

In this project, I have used a Grafbase connector to set up Contentful service using the Grafbase configuration file:-

```typescript
import { g, connector, config } from '@grafbase/sdk';

const contentful = connector.GraphQL({
  url: g.env('CONTENTFUL_API_URL'),
  headers: (headers) => {
    headers.set('Authorization', `Bearer ${g.env('CONTENTFUL_API_TOKEN')}`);
  },
});

g.datasource(contentful, { namespace: 'Contentful' });

export default config({
  schema: g,
});
```

Next, I used Pathfinder from Grafbase to generate graphQL queries:-

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692089783985/ce9a5bbe-9c0b-4f77-96e7-383996e0e471.png align="center")

I used these queries in the frontend Next.js app using `urql` npm package:-  

```javascript
import {
  Client,
  Provider,
  cacheExchange,
  fetchExchange,
  gql,
  useQuery,
} from 'urql';
const client = new Client({
  url: 'grapql-url',
  exchanges: [cacheExchange, fetchExchange],
});

const GetBlogs = gql`
  query Contentful {
    contentful {
      subatomicaBlogPostCollection {
        total
        items {
          blogTitle
          blogDescription
          blogImage {
            url
          }
          postnumber
        }
      }
    }
  }
`;
```

## Project Demo Video

%[https://youtu.be/GF99_W_Ue84] 

## Project screenshots

Home Page View:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097189367/a6bd0548-b30a-4de0-9203-94e8f6cd8e13.png align="center")

Article view:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097268140/390cf29c-0b79-440a-9533-44713516a26c.png align="center")

Responsive View:-

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097404460/b6cdbc16-120a-44c6-a07d-0840c31e2e95.png align="center")

## How to use this project

Here are the steps to use this project for your own topics:-

1. Create an account on [Contentful](https://www.contentful.com/) website
    
2. Next, create a content model for a blog of your choice and publish the model with the required fields:-
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692091866994/7a658a3c-c4c8-4507-bbb6-7b1cbdc57830.png align="center")
    
3. Next, create an entry for a blog post in the content section and publish the entry:-
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692091922116/1836a946-2dc0-4320-b098-b97ba0d8b40e.png align="center")

1. Now clone the repo from the below URL:-  
    [https://github.com/saurabhnative/subatomica](https://github.com/saurabhnative/subatomica)
    
2. Create a *.env* file with two variables from Contentful website viz `CONTENTFUL_API_URL` and `CONTENTFUL_API_TOKEN` which can be found on Contentful website.
    
3. Run `yarn` or `npm install` command to install relevant packages.
    
4. Run the below commands to setup Grafbase locally:-  
    Execute the command `npx grafbase dev` on the project and navigate to [http://127.0.0.1:4000](http://127.0.0.1:4000) to execute queries and mutations with Pathfinder.
    
5. You can start the Next.js project using `yarn dev` command. Make necessary changes to GraphQL queries based on your blog requirements and publish the repo to Github.
    

## Deployment to production

Follow these steps to deploy to production:

1. Signup for an account at [**grafbase.com**](http://grafbase.com)
    
2. Visit [**grafbase.com/new**](http://grafbase.com/new) to create a new project
    
3. Connect and deploy your application where the `grafbase` was added
    
4. Make sure to add your `CONTENTFUL_API_URL` and `CONTENTFUL_API_TOKEN` to environment variables while deploying to Grafabase
    
5. You will receive a Graphbase URL once the project is live on Grafbase. Add the URL in the Next.js project and deploy to Vercel to make the project live.
    

## Project Links

You can access the project on below URL:-  
[https://subatomica.vercel.app/](https://subatomica.vercel.app/)  
  
GitHub repo for the project can be found here:-  
[https://github.com/saurabhnative/subatomica](https://github.com/saurabhnative/subatomica)

## Conclusion

I had a lot of fun while building this project and it did improve my grasp on a lot of project development fundamentals. Best of luck to everyone participating in the hackathon and have a nice day ahead 😁