## Compressing images in your react app programmatically

Hello curious stranger on the internet, today I am going to show a short and simple way to compress images for your react website. 
The typical use case for this in my case was that I was using images downloaded from  [Pixabay](https://pixabay.com/)  and  [Pexels](https://www.pexels.com/)  website for my web app. The problem was that even after downloading images in smallest possible resolution from the websites, the images would get loaded with noticeable lag on the website from image CDN even on faster internet connections.

So I decided to use  [imagemin](https://www.npmjs.com/package/imagemin)  npm module for compressing images.

First install imagemin related npms in your react project dev-dependencies:-
```
npm install --save-dev imagemin imagemin-jpegtran imagemin-pngquant
```
Here the two additional npms are for JPEG and PNG files.  

The process is pretty straightforward from here on:-

First we create a `imagemin.mjs` file at project level with the below content:-

```
import imagemin from "imagemin";
import imageminJpegtran from "imagemin-jpegtran";
import imageminPngquant from "imagemin-pngquant";

// replace build/images with your own path if needed
const files = await imagemin(["./build/images/*.{jpg,png,jpeg}"], {
  destination: "./build/images/",
  plugins: [
    imageminJpegtran(),
    imageminPngquant({
      quality: [0.6, 0.8],
    }),
  ],
});

console.log(files);
```

This script will look for images in source image directory which we specify and add compressed files in destination folder.
In case would like to compress images in final build folder you can set source and destination as `build` folder as shown above.
Next try to run the script once to verify that it works by running the below command:-
```
node imagemin.mjs
```

Now we can add this as a process in the `package.json` file in our react app as shown below:-
```
...
// postbuild task added to run our script
"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "postbuild": "node imagemin.mjs"
  },
```

Now each time we make a build using `npm run build` command, we can run the `postbuild` command later to compress the images in final build directory.
We can even club the two commands into a single command as well.

This is one of the ways in which we can compress images in create-react-app without ejecting it.
Kindly upvote the article if you found it useful and follow me for more such articles in future.