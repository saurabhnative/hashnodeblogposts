## Introducing README gen - Most advanced README generator for your opensource projects ✨️

# Hello Everyone
Hope you all are safe and doing well in your life. I am  [Saurabh Mhatre](https://hashnode.com/@saurabhmhtr), an experienced frontend developer trying new technologies every month.
I am super excited to announce my latest side project,  [**README Gen**](https://readme-gen.vercel.app/). This is my submission for  [**Auth0 Hackathon on Hashnode**](https://townhall.hashnode.com/auth0-hackathon?source=events_widget). I built this project taking time out after my day-to-day job for over a month and today I am pretty excited to showcase all the features this product has to offer for improving your Github project README files.

## Why I built README gen?
A lot of job seekers today use Github to showcase their projects and skills to prospective recruiters. However, the README files added to this project are often very basic. A few months back I researched a lot about which sections we should include in our README files for improving the Github project presentation. I came up with a list of around 10 important sections after the research which are listed down in this article:-  [10 useful sections for Github READMEs](https://saurabhnative.hashnode.dev/10-useful-sections-to-improve-your-github-readme-files). However, remembering and adding these 10 sections each time seemed like too many efforts. 
So I built [README gen](https://readme-gen.vercel.app/) for helping people to add these 10 important sections faster with an easy to use forms-based interface.

## Introducing README gen
README Gen is a tool to build amazing README files for your open source project faster than ever before. You can use this tool to create a structured README quickly with an easy to use forms-based interface.

%[https://youtu.be/An6bmCHy7Q0]

I mainly built this tool to help students trying to showcase frontend/full-stack projects for job interviews in a much better manner.
Hope this helps someone in improving their chances of clearing the interview process.
Others can also use this tool to build the README files for frontend/full-stack projects in a properly structured manner in the shortest time possible.
If you have any suggestions feel free to mention them in the comments or reach out to me on my social handles mentioned below.

 [**Github Repo**](https://github.com/saurabhnative/create-frontend-readme)  |  [**Live Demo**](https://readme-gen.vercel.app/) 

## Let's talk about some amazing features

- ### Easy to use collapsible menus for all 10 essential sections

![CollapsibleMenus.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1630136009485/x-F6k7GSl.gif)

The entire README creation process is divided into a systematic 10 steps process where users can add details using simple form-based inputs. 

- ### Resizable image screenshots

![ResizableImages.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1630142429158/VtVJ2_Xjp.gif)
With README gen you can attach unlimited project screenshots and change width and height as well.

- ### Markdown Editing mode for better customisation
Although form-based input is sufficient for a decent README file if you ever feel the need to customise the README output further, simply switch to markdown mode and start editing any sections right away.

![MarkdownMode.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1630142378271/61XI0VoXz.gif)

- ### Preview section for generated code
You can see the actual code which will be added to your README File by switching to code preview mode as well.

![CodePreviewMode.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1630142763915/4PFl-yvz3.gif)
 
- ### Copy Github README code in a single click 
Updating your project README is simple with just a single click to copy-paste the generated code

![SingleClickCopy.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1630143072101/GPJOppUoK.gif)

- ### Responsiveness
README Gen is a responsive web app so that you can access from your mobile phone anytime with ease.

![Responsive.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1630388212742/hz9BHqbYa.gif)

## Technologies used


*  [Next.js](https://nextjs.org/) 
*  [TailwindCSS](https://tailwindcss.com/)  
*  [Auth0 for user authentication](https://auth0.com/docs/quickstart/webapp/nextjs) 
*  [react-collapsible](https://www.npmjs.com/package/react-collapsible)  - For collapsible menu items
*  [react-icons](https://www.npmjs.com/package/react-icons)  - For icons used in different sections
*  [react-markdown](https://www.npmjs.com/package/react-markdown)  - For markdown preview
*  [react-tagsinput](https://www.npmjs.com/package/react-tagsinput)  - For taking multiple input items at once
*  [react-toastify](https://www.npmjs.com/package/react-toastify)  - For toast notification
*  [turndown](https://www.npmjs.com/package/turndown)  - For HTML to markdown conversion

## Planning, Design and Development process
I was planning to build a tool for freshers and experienced professionals to write README files in a better-organised manner for a long time. Also, personally, I make a lot of frontend/full-stack projects in my spare time so this tool would be helpful for my own future projects as well.
I started off with building a really basic design on Figma. My designing skills are not that great so I try to come up with a decent design with my best efforts. The first version of the design in Figma is shown below:-

![Screenshot 2021-08-29 at 1.07.59 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630222684318/sdlhfBRW3.png)

I built this project first to test out what all packages and technologies would work best for the project. Then I went back to the Figma draft and built a better one which is now showcased in the actual project.
This was the design version 2 of the same project:-

![Screenshot 2021-08-29 at 1.10.12 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630222817768/vnS-gARy0.png)

You can view both the designs here:-  [README gen figma design](https://www.figma.com/file/ZJvMh73FRagYrTAjcSFBkr/CreateFrontendREADME?node-id=0%3A1) 

Next came the actual development process. I have wanted to try out Next.js for a long time and this hackathon seemed like the best opportunity to learn it.

I used the `create-next-app` CLI tool to start off with the project and built the left section form elements using Tailwind CSS template by Next.js team:-

```
npx create-next-app -e with-tailwindcss readme-gen
``` 

In the right section, the first challenge was to convert form inputs to markdown text. After failing to find the right module to do this directly in a proper manner, I came with the solution of using two different npms for the purpose.
The first one was [**turndown**](https://www.npmjs.com/package/turndown) npm which can convert HTML tags to markdown. The next one was [**react-markdown**](https://www.npmjs.com/package/react-markdown) which can show a markdown preview on a website.

```javascript
// Turndown code usage to convert HTML to markdown
const turndownService = new TurndownService({ codeBlockStyle: "fenced" });
const markdown = turndownService.turndown(readmeContent);

// react-markdown to show markdown in website
import ReactMarkdown from "react-markdown";
...
<ReactMarkdown
   children={markdown}
/>
```

Once the basic form elements were ready, I used [**react-collapsible**](https://www.npmjs.com/package/react-collapsible) to group form elements into collapsible menu items

```
import Collapsible from "react-collapsible";
...
<Collapsible
          trigger="Step 1: Add title, description and socialify image(optional)"
          open={true}
 >
// form elements
</Collapsible>
```

The last part to take care of was [Auth0](https://auth0.com/) integration. The documentation for Next.js integration was pretty straightforward from the official [docs](https://auth0.com/docs/quickstart/webapp/nextjs). I did a lot of customisations on the login page like inserting my own logo and app name quite easily from Auth0 dashboard.
Inserting Auth0 code in project was easy as well:-

```
import { UserProvider } from "@auth0/nextjs-auth0";
...
<UserProvider>
      <Component {...pageProps} />
</UserProvider>
```

ENV file setup for Auth0 constants
```
AUTH0_SECRET="secret"
AUTH0_BASE_URL="site-url"
AUTH0_ISSUER_BASE_URL='https://YOUR_DOMAIN'
AUTH0_CLIENT_ID='YOUR_CLIENT_ID'
AUTH0_CLIENT_SECRET='YOUR_CLIENT_SECRET'
```

And finally, I had to add server side functions in API folder

```
import { handleAuth } from "@auth0/nextjs-auth0";

export default handleAuth();
```

The rest of the process was simply adding relevant URLs for login/logout buttons from the section of the official docs. I personally thought that authentication would take the longest time but in reality, it took the least time in the entire development process.

The entire design and building took almost a month of me working after my day to day job. You can check out the complete codebase here: [README gen Github Repo](https://github.com/saurabhnative/create-frontend-readme).

For deployment, I simply connected the Github project to  [Vercel](https://vercel.com/) and the rest of the deployment was seamlessly taken care of in the Vercel dashboard. 


> You can check out README gen live demo here: https://readme-gen.vercel.app/

## Challenges faced


### 1. HTML to Markdown code conversion
I could not use simple text to markdown converters since elements like project title in bold and image previews needed to be handled. Luckily [**turndown**](https://www.npmjs.com/package/turndown) npm helped a lot in converting HTML code to markdown. The best thing was the customisation options available by which I was able to create README files just the way I wanted them to.

### 2. Maintaining order of final sections in README
Users can start from any section on the left and end at any section. However, I cannot add the contribution section before let's say project title and description. For solving this problem I created a custom JSON object with indexes to maintain the final section order in README files. You can find the custom JSON here: [Custom Object](https://github.com/saurabhnative/create-frontend-readme/blob/main/constants/utils.js)

### 3. Responsiveness
To handle responsiveness, Tailwind CSS helped a lot. The custom classes allowed to to iterate faster and build responsive design quicker as well.

## Competitor Analysis
There are a lot of online markdown editors available like  [Dillinger](https://dillinger.io/). However, none of them have a form-driven interface specifically designed for creating Github READMEs. Since [README gen](https://readme-gen.vercel.app) also supports markdown mode it can be used as an online markdown editor as well. But the ease of use in creating README files faster with form-based inputs sets it apart from existing products. 
I made the README gen's 10 step process after going through a lot of awesome Github projects and understanding what sets them apart from other ones. And if anyone wants to customise the data in form-driven steps, they can easily do it by switching to markdown mode. So this 10 step process is a unique selling point(USP) feature in this project which makes it different and useful for every open-source contributor.

## Licensing and Contribution
This project is licensed under  [MIT](https://github.com/saurabhnative/create-frontend-readme/blob/main/LICENSE) 

You can contribute to this project using standard [Github flow](https://guides.github.com/introduction/flow/).

I have also enabled the  [discussions](https://github.com/saurabhnative/create-frontend-readme/discussions)  section in case you would like to share your own ideas or discuss any topics related to this project code.

## Sample README generated using this project
You can find a sample README generated using this project here:  [Stories Feed Github](https://github.com/saurabhnative/storiesfeedapp

Short Preview:

![Screenshot 2021-08-29 at 1.52.42 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630225370862/zxYVyKBPr.png)


Feel free to connect with me on social handles:
-  [**Twitter**](https://twitter.com/saurabhnative) 
-  [**Instagram**](https://www.instagram.com/saurabhnative/?hl=en)
-  [**Github**](https://github.com/saurabhnative) 

## Feedback
Thank you so much for checking out [**README gen**](https://readme-gen.vercel.app/). Your feedback is going to help me a lot in improving  [**README gen**](https://readme-gen.vercel.app/) further and motivate me to build more features as well. So let me know your views on the project.




 







