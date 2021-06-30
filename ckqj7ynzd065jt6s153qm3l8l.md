## Food delivery website using HERN stack

**Motivation behind the project**

With recurrent lockdown situations in many part of the world, restaurant industry has suffered a lot. Most of the restaurants are now switching to take away and online delivery platforms to sustain their business. I have tried to build a simple food delivery website to help such businesses using HERN(HarperDB, Express, React, Node) stack. 
You can see the preview of the final website below:-

%[https://youtu.be/dnji_DxST7s]

**Tech Stack Used**

- React.js for frontend website
- Node(Express.js) for backend server
- HarperDB for storing data

You can find code for the website in the below Github repos:-

Frontend code:- [Github](https://github.com/saurabhnative/foodDeliveryAppFrontend)   
Backend code:- [Github](https://github.com/saurabhnative/foodDeliveryAppBackend)

Screens:-

1. Home screen where users can browse through different category of food items:-
![HomeScreen.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625040112026/GlSS83SWu.png)

2. Individual food items screen from where users can place there orders:-
![FoodItemsScreen.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625040234263/eZyAVo9BH.png)

3. Orders/Cart screen in which we can remove placed orders and place final order:-
![OrdersScreen.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625040300440/uWGNincQk.png)

The frontend part is built in react.js using [create-react-app](https://reactjs.org/docs/create-a-new-react-app.html) CLI tool. There are individual components for header, home screen, food items and cart screen. I have used `axios` npm to transfer data to and from the backend server. I have also used react-router for handling different routes in the website. 

The backend server is built using [express-generator](https://expressjs.com/en/starter/generator.html) CLI tool. It mainly consists of four [routes](https://github.com/saurabhnative/foodDeliveryAppBackend/blob/main/routes/delivery.js):-

`/getAllItems` for listing food items in website

`/add` for allowing user to place order

`/delete` for allowing users to remove a placed order

`/getAllOrders` to list all current user orders

If you would like to use this project in your future learnings then make sure to add relevant environment variables used in the frontend and backend repositories. If you face any issues while using the codebase feel free open a discussion thread/issue on the related Github repo.

If you found this article or project useful, hit the like button, follow my blog, and if there is anyone you know who will benefit from such projects please share it with them as well.

I would love to connect with you on [Twitter](https://twitter.com/saurabhnative) or [Instagram](https://www.instagram.com/saurabhnative/).

 Goodbye and have a nice day.


