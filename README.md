# Scrap Platform Documentation

Welcome to the GitHub documentation for the Scrap Platform, a React-based web application designed for customers to list their scrap items and for vendors to get orders for scrap collection. This documentation will guide you through the setup, components, and features of the platform. 
# Visit My Website at:
[Eco Raddi](https://ecoraddi.netlify.app/)
## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Components](#components)
  - [Navbar](#navbar)
  - [Master](#master)
  - [Details](#details)
  - [Form](#form)
  - [Done](#done)
  - [BlogDetails](#blogdetails)
  - [Order](#order)
  - [Price](#price)
  - [Blogs](#blogs)
- [Routing](#routing)
- [Contributing](#contributing)
- [License](#license)

## Introduction

The Scrap Platform is a user-friendly web application where customers can list various types of scrap items like metal, paper, and electronics. Vendors can browse these listings and fulfill orders for scrap collection. The platform provides real-time scrap rates and customer testimonials to ensure a smooth and trustworthy experience.

## Features

- **Scrap Listing:** Customers can list different types of scrap items.
- **Vendor Orders:** Vendors can view and fulfill orders for scrap collection.
- **Real-time Scrap Rates:** The application displays real-time rates for different scrap materials.
- **Customer Testimonials:** The platform showcases testimonials from satisfied customers.
- **Blog Section:** Contains informative blogs related to scrap and recycling.

## Installation

To set up the project locally, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/utsavmehta24/EcoRaddi.git
   ```
2. Navigate to the project directory:
   ```bash
   cd EcoRaddi
   ```
3. Install the dependencies:
   ```bash
   npm install
   ```
4. Start the development server:
   ```bash
   npm start
   ```

## Project Structure

The project is structured as follows:

```
EcoRaddi/
├── src/
│   ├── components/
│   │   ├── BlogDetails/
│   │   ├── Blogs/
│   │   ├── done/
│   │   ├── form/
│   │   ├── Navbar/
│   │   ├── Details/
│   │   ├── Orders/
│   │   ├── price/
│   │   └── ...
│   ├── App.jsx
│   ├── main.jsx
│   └── master.jsx
│
└── package.json
```

## Components

### Navbar

The `Navbar` component is an essential part of the Scrap Platform, providing easy navigation for users. It features a responsive design with a collapsible hamburger menu for mobile users, ensuring that the navigation links are accessible across all device types.

- **Location**: `src/components/Navbar/Navbar.js`
- **Key Features**:
  - **Responsive Design**: Automatically adapts to screen sizes, displaying a hamburger menu on smaller screens for better usability.
  - **Navigation Links**: Includes links to main sections of the application (`Home`, `Price`, `About`, `Place Order`, `Work With US??`), enabling seamless user navigation.
  - **Dynamic Routing**: Utilizes `react-router-dom` for efficient and smooth client-side routing.
  - **Hooks for State Management**: Uses `useRef` to reference DOM elements and `useEffect` to manage the event listener for toggling the navigation menu.
  - **Easy Customization**: Styled with an external CSS file (`navbar.css`), allowing for straightforward updates to the look and feel.

The `Navbar` consists of an image logo and several navigation links, making it easy for users to explore different sections of the platform. The hamburger menu is linked to an event listener that toggles the `active` class, controlling the visibility of the menu items on smaller screens.

```jsx
import React, { useEffect, useRef } from 'react';
import { Link } from 'react-router-dom';
import img from './logo.png';
import './navbar.css';

function Navbar() {
  const hamMenuRef = useRef(null);
  const mainNavbarRef = useRef(null);

  useEffect(() => {
    const hamMenu = hamMenuRef.current;
    const mainNavbar = mainNavbarRef.current;

    const toggleActive = () => {
      hamMenu.classList.toggle('active');
      mainNavbar.classList.toggle('active');
    };

    hamMenu.addEventListener('click', toggleActive);

    return () => {
      hamMenu.removeEventListener('click', toggleActive);
    };
  }, []);

  return (
    <div className="master-main-navbar">
      <div className="navbar-container">
        <div className="main-navbar" ref={mainNavbarRef}>
          <img className="navbar-image" src={img} alt="navbar-logo" />
          <Link to="/" className="item">Home</Link>
          <Link to="/price" className="item">Price</Link>
          <Link to="/about" className="item">About</Link>
          <Link to="/form" className="item">Place Order</Link>
          <Link to="/order" className="item">Work With US??</Link>
        </div>
        <div className="hem-menu" ref={hamMenuRef}>
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
    </div>
  );
}

export default Navbar;
```

The component uses custom CSS classes like `item`, `main-navbar`, `navbar-container`, etc., for styling, defined in `navbar.css`.

This component ensures that users have a consistent and efficient navigation experience across the Scrap Platform, whether they are accessing it on a desktop or a mobile device.
**File:** `src/components/Navbar/Navbar.js`

### Master

The `Master` component serves as the landing page of the application, introducing users to the platform and its features.
```jsx
import React from 'react';
import Home from './componets/Home/Home';
import Works from './componets/Works/works';
import Whyus from './componets/Why_Us/Why_us';
import Usage from './componets/Usage/usage';
import Testmonials from './componets/Testmonials/Testmonials';
import Blogs from './componets/Blogs/Blogs';
import Price from './componets/price/price';
import 'bootstrap/dist/css/bootstrap.min.css';

function Master() {
    return (
        <>
            <Home />
            <Price />
            <Works />
            <Whyus />
            <Usage />
            <Testmonials />
            <Blogs />
        </>
    );
}

export default Master;
```
**File:** `src/master.js`

### Details

The `Details` component displays customer testimonials and detailed information about the scrap platform.

The `Details.jsx` component is a functional React component that serves as a footer section for a web page. It includes contact information, links to social media, project details, and the company's address. The component is styled using the `Details.css` stylesheet and utilizes several other React components and assets.

## Usage

The `Details.jsx` component can be imported and used in any React component where a footer is required.

```jsx
import Footer from './Details';
```

### Dependencies

- **React**: The component is built using the React library.
- **react-router-dom**: Used for navigation within the app.
- **CSS**: Styles are imported from `Details.css`.
- **Images**: An image is imported from `logo.png`.

### Component Code

```jsx
import React from "react";
import './Details.css';
import Blogs from "../Blogs/Blogs";
import imagelogo from './logo.png';
import { Link } from "react-router-dom";

const Footer = () => {
    return (
        <footer className="footer_section">
            <div className="container12 footer_container">
                <div className="row12 footer_padding">
                    <div className="col-md-4">
                        <p className="contact_us">Contact Us</p>
                        <p><a href="tel:+919913816941">+91 9913816941</a></p>
                        <p><a href="mailto:ecoraddi1@gmail.com">ecoraddi1@gmail.com</a></p>
                        <p style={{ fontWeight: '700' }}>Customer Support available <br />from 10am - 7pm</p>
                        <p className="find_us">Find Us Here</p>
                        <ul className="find_us_ul">
                            <li><a href="/" target="_blank" rel="noreferrer"><img src="https://ikp.edgekit.net/y8s2vhk66ef/image_2_Bi5cqcyBFNT.png?updatedAt=1628624823915" alt="instagram" /></a></li>
                            <li><a href="/" target="_blank" rel="noreferrer"><img src="https://ikp.edgekit.net/y8s2vhk66ef/image_3_yByOZld4XFh.png?updatedAt=1628624824789" alt="twitter" /></a></li>
                            <li><a href="/" target="_blank" rel="noreferrer"><img src="https://ikp.edgekit.net/y8s2vhk66ef/image_6_zHp_XCLcq9Z.png?updatedAt=1628624826605" alt="linkedin" /></a></li>
                            <li><a href="/" target="_blank" rel="noreferrer"><img src="https://ikp.edgekit.net/y8s2vhk66ef/image_5_3EElSEX6sCW.png?updatedAt=1628624825705" alt="facebook" /></a></li>
                        </ul>
                    </div>
                    <div className="col-md-4">
                        <p className="contact_us">A Project By DS and AI Team</p>
                        <a href="https://play.google.com/store/apps/details?id=com.swapeco.app" target="_blank" rel="noreferrer">
                            <img style={{ height: '13%', width: '50%' }} src="https://capsource-bucket.s3.us-west-2.amazonaws.com/wp-content/uploads/2021/04/02172234/DPU-Logo-1.png" alt="playstore" />
                        </a>
                        <p className="company"><a href="/"><Link to="/price">Scrap Rates</Link></a></p>
                        <p className="cursor-pointer"><a href="/" target="_blank" rel="noreferrer"><Link to={"/blogs"}>Blogs</Link></a></p>
                    </div>
                    <div className="col-md-4 footer-address">
                        <img className="logo_class" src={imagelogo} alt="Scrapuncle" />
                        <p className="swapeco"><b>rockingUT Solutions Fun. Limited </b></p>
                        <p style={{ display: 'block' }}>
                            <b>Regd. Address:</b> <br />Dr. D.Y. Patil Instiute of technology, Sant Tukaram Nagar, Pimpri Pune-411018
                        </p>
                        <p style={{ display: 'block' }}>
                            <br /><b>Corr Address:</b><br />Dr. D.Y. Patil Instiute of technology, Sant Tukaram Nagar, Pimpri Pune-411018
                        </p>
                    </div>
                </div>
            </div>
        </footer>
    );
};

export default Footer;
```

## Structure and Styling

The component is divided into three main sections, each within a Bootstrap column (`col-md-4`):

1. **Contact Information**: Includes phone, email, and customer support details.
2. **Project Information**: Details about the project and links to related pages like "Scrap Rates" and "Blogs".
3. **Company Address**: Displays the company's logo and both registered and correspondence addresses.

The component uses custom CSS classes like `footer_section`, `container12`, `row12`, etc., for styling, defined in `Details.css`.

## External Links

- **Social Media Icons**: Links to Facebook.
# Notes

- The component uses hardcoded links and images which should be replaced with actual URLs and paths in a production environment.
- Ensure `Details.css` is properly included to apply the necessary styles.
- The component includes static content, making it suitable for a footer section on static or dynamic pages.

## Contact

For any questions or issues, please contact [ecoraddi1@gmail.com](mailto:ecoraddi1@gmail.com).
### Form

The `Form` component is a crucial part of the scrap-collecting platform. It facilitates the collection of user information and scrap item details, allowing users to schedule a scrap collection. The form ensures data validation and handles form submissions by sending the data to a backend server.

### File Structure

- **Component File**: `form.js`
- **CSS File**: `form.css`

## Usage

### Importing the Component

To use the `Form` component, import it into your React application as follows:

```jsx
import Form from './form';
```

### Example Usage

```jsx
import React from 'react';
import Form from './form';

function App() {
    return (
        <div className="App">
            <Form />
        </div>
    );
}

export default App;
```

## Component Details

### State Variables

The `Form` component maintains several state variables using the `useState` hook:

- **name**: Stores the user's full name.
- **email**: Stores the user's email address.
- **address**: Stores the user's address.
- **city**: Stores the user's city.
- **state**: Stores the user's state.
- **zip**: Stores the user's zip code.
- **Weight**: Stores the approximate weight of the scrap (default: `3kg`).
- **MobileNumber**: Stores the user's mobile number.
- **anySpecification**: Stores any additional specifications provided by the user.
- **selectedDate**: Stores the selected date for scrap collection.
- **selectedTime**: Stores the selected time for scrap collection.
- **selectedItems**: Stores the selected scrap items.

### Validation State Variables

The component also maintains state variables for error messages:

- **emailError**
- **nameError**
- **mobilenumberError**
- **addressError**
- **stateIndiaError**
- **zipError**
- **cityError**

### Event Handlers

- **handleCheckboxChange**: Handles the selection of scrap items.
- **handleKeyDown**: Submits the form when the Enter key is pressed.
- **handleSubmit**: Validates form inputs and submits the form.

### Form Validation

The form includes validation for the following fields:

- **Email**: Must follow a valid email format.
- **Mobile Number**: Must be a valid 10-digit number.
- **Name**: Must only contain letters and spaces.
- **Address**: Must be a valid address format.
- **State**: Must only contain letters and spaces.
- **Zip Code**: Must be a valid 6-digit code.
- **City**: Must only contain letters and spaces.

### Form Submission

Upon form submission, the data is sent to a backend server:

```js
fetch('http://localhost:8000/Details', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(newCustomer)
})
.then(response => response.json())
.then(data => {
    // Handle successful response here
})
.catch(error => {
    // Handle errors here
});
```

### Navigation

After successful submission, the user is navigated to the `/done` route:

```js
navigate('/done');
```

## Component Structure

The `Form` component consists of the following sections:

- **Billing Address**: Captures user's personal and address details.
- **Item Details**: Allows users to select scrap items and specify details.
- **Payment Method**: Provides options for card payments, cash, and UPI transfers.

### Billing Address

Captures details like full name, mobile number, email, address, city, state, and zip code.

### Item Details

Includes options for selecting scrap items, specifying weight, date, and time for collection, and adding any additional specifications.

#### CSS Styling

The component uses `form.css` for styling. Ensure to include this CSS file for proper styling.

### Example CSS Import

```css
import './form.css';
```

### Backend Server

Ensure the backend server is running on `http://localhost:8000` to handle the form submission.

###### Conclusion

The `Form` component is a well-structured and validated form for scheduling scrap collection. It captures essential user and scrap details and provides multiple payment options, making it a comprehensive solution for the scrap-collecting platform.

**File:** `src/components/Form/Form.jsx`

### Done

The `Done` component displays a confirmation message after a customer has successfully listed their scrap items.

**File:** `src/components/Done/Done.jsx`

### BlogDetails

The `BlogDetails` component is responsible for displaying detailed information about a specific blog post on the scrap-collecting platform. It fetches and renders the blog details based on the provided blog ID from the URL. The blog data is retrieved from a local JSON file.

### File Structure

- **Component File**: `BlogDetails.js`
- **CSS File**: `ArticleDetails.css`
- **Data File**: `BlogsData.json`

## Usage

### Importing the Component

To use the `BlogDetails` component in your React application, import it as follows:

```jsx
import BlogDetails from './BlogDetails';
```

### Example Usage

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import BlogDetails from './BlogDetails';

function App() {
    return (
        <Router>
            <Routes>
                <Route path="/blog/:id" element={<BlogDetails />} />
            </Routes>
        </Router>
    );
}

export default App;
```

## Component Details

### State Variables

The `BlogDetails` component uses the `useState` hook to manage its state:

- **article**: Stores the fetched blog details.

### Effect Hook

The component utilizes the `useEffect` hook to fetch the blog details whenever the `id` parameter changes:

```jsx
useEffect(() => {
    fetchBlogDetails();
}, [id]);
```

### Fetching Blog Details

The `fetchBlogDetails` function retrieves the blog details from the local `BlogsData.json` file based on the blog ID:

```js
const fetchBlogDetails = async () => {
    try {
        const data = BlogsData.find(blog => blog.id === Number(id));
        console.log('Fetched Blog details:', data);
        setArticle(data);
    } catch (error) {
        console.error('Error fetching article details:', error);
    }
};
```

### Conditional Rendering

The component displays a loading message until the blog details are fetched:

```js
if (!article) {
    return <div>Loading...</div>
}
```

### Rendering the Blog Article

The blog details are displayed with the following structure:

- **Image**: The blog's image is displayed at the top.
- **Title**: The blog's title is shown below the image.
- **Description**: The blog's description is split into paragraphs and rendered line by line.

```jsx
return (
    <div className='blog-article'>
        <h1><img src={article.image} alt={`photo-of-${article.title}`} /></h1>
        <p className='blog-article-title'>{article.title}</p>
        {article.description.split('\n').map((line, index) => (
            <p key={index} className='blog-article-description'>{line}</p>
        ))}
    </div>
);
```

## Component Structure

The `BlogDetails` component comprises:

- **Blog Image**: Displays an image related to the blog post.
- **Blog Title**: Displays the title of the blog post.
- **Blog Description**: Renders the blog's description, split into paragraphs for readability.

### JSON Data

Ensure the `BlogsData.json` file is correctly formatted and placed in the appropriate directory.

##### Conclusion

The `BlogDetails` component is designed to fetch and display detailed information about a specific blog post. It handles fetching data from a local JSON file and ensures that the blog content is displayed in a user-friendly manner. By following this documentation, you should be able to effectively integrate and use the `BlogDetails` component in your scrap-collecting platform.
**File:** `src/components/BlogDetails/BlogDetails.jsx`

### Order

The `Order` component is designed to display a list of orders retrieved from a backend server and provides functionality to delete specific orders. This component is a key part of a scrap-collecting platform, where users can view and manage orders efficiently.

### File Structure

- **Component File**: `Order.js`
- **CSS File**: `order.css`

## Usage

### Importing the Component

To use the `Order` component in your React application, import it as follows:

```jsx
import Order from './Order';
```

### Example Usage

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Order from './Order';

function App() {
    return (
        <Router>
            <Routes>
                <Route path="/orders" element={<Order />} />
            </Routes>
        </Router>
    );
}

export default App;
```

## Component Details

### State Variables

The `Order` component uses the `useState` hook to manage its state:

- **orders**: Stores the list of orders fetched from the server.

### Effect Hook

The component utilizes the `useEffect` hook to fetch the list of orders when the component mounts:

```jsx
useEffect(() => {
    fetch('http://localhost:8000/Details')
        .then(response => response.json())
        .then(data => setOrders(data))
        .catch(error => console.error('Error fetching data:', error));
}, []);
```

### Fetching Orders

The component fetches the orders from the backend server using the `fetch` API:

```js
useEffect(() => {
    fetch('http://localhost:8000/Details')
        .then(response => response.json())
        .then(data => setOrders(data))
        .catch(error => console.error('Error fetching data:', error));
}, []);
```

### Deleting Orders

The `handleDelete` function is responsible for removing an order both from the UI and the backend server:

```js
const handleDelete = (orderId) => {
    setOrders(orders.filter(order => order.id !== orderId));

    fetch(`http://localhost:8000/Details/${orderId}`, {
        method: 'DELETE',
    })
        .then(response => {
            if (!response.ok) {
                console.error('Error deleting order:', response.statusText);
            }
        })
        .catch(error => console.error('Error deleting order:', error));
};
```

### Displaying Orders

The orders are displayed in a structured format with all relevant details:

```jsx
return (
    <div className="order-main-section">
        <h1>Order</h1>
        <div className="order-list">
            {orders.map(order => (
                <div key={order.id} className="order-item">
                    <h2>{order.name}</h2>
                    <p>Email: {order.email}</p>
                    <p>Address: {order.address}, {order.city}, {order.state}, {order.zip}</p>
                    <p>Weight: {order.Weight}</p>
                    <p>Mobile Number: {order.MobileNumber}</p>
                    <p>Any Specification: {order.anySpecification}</p>
                    <p>Selected Date: {order.selectedDate}</p>
                    <p>Selected Time: {order.selectedTime}</p>
                    <p><button onClick={() => handleDelete(order.id)}>Take Order</button></p>
                </div>
            ))}
        </div>
    </div>
);
```

## Component Structure

The `Order` component comprises:

- **Order List**: A list of order items fetched from the server.
- **Order Item**: Each order item displays details such as name, email, address, weight, mobile number, specifications, selected date, and time.
- **Delete Button**: Each order item has a "Take Order" button that allows the order to be deleted.

## CSS Styling

The component uses `order.css` for styling. Ensure to include this CSS file to apply the correct styles.

### CSS Import

```css
import './order.css';
```

#### Ensure the backend server is running and accessible at `http://localhost:8000/Details` to fetch and delete orders.

### Handling Errors

- **Fetching Data**: Handle errors in case of failed fetch requests.
- **Deleting Orders**: Handle errors if the delete operation fails.

##### Conclusion

The `Order` component is essential for managing and displaying orders in a scrap-collecting platform. It effectively fetches orders from a backend server and allows for the deletion of orders, providing an intuitive interface for users. By following this documentation, you should be able to effectively integrate and use the `Order` component in your application.

**File:** `src/components/Order/Order.jsx`

### Price

The `Price` component is a React component that displays the best price for various types of scrap materials. The prices are dynamically updated using the `CountUp` animation library to provide a visually engaging user experience. The component also uses `VisibilitySensor` to ensure that the price animation only occurs when the element is visible on the screen.

### File Structure

- **Component File**: `Price.js`
- **CSS File**: `price.css`

## Usage

### Importing the Component

To use the `Price` component in your React application, import it as follows:

```jsx
import Price from './Price';
```

### Example Usage

```jsx
import React from 'react';
import Price from './Price';

function App() {
    return (
        <div className="App">
            <Price />
        </div>
    );
}

export default App;
```

## Component Details

### State Variables

The `Price` component uses the `useState` hook to manage its state:

- **key**: Used to trigger re-rendering of the `CountUp` component for animation purposes.
- **loopCount**: Tracks the number of times the animation has looped. The animation will loop up to 5 times.

### Reset Animation

The `resetAnimation` function is used to restart the price count-up animation up to 5 times with a 2-second delay:

```jsx
const resetAnimation = () => {
    if (loopCount < 5) {
        setTimeout(() => {
            setKey(prevKey => prevKey + 1);
            setLoopCount(prevCount => prevCount + 1);
        }, 2000); // 2 seconds delay
    }
};
```

### Displaying Prices

The component displays prices for different types of scrap materials with icons and animated values:

```jsx
return (
    <div className="price-component">
        <h1>Best Price</h1>
        <h2 className="item-price">
            <img src="https://icon-library.com/images/paper-icon-png/paper-icon-png-27.jpg" alt="paper icon" />
            Paper: ₹<VisibilitySensor>
            <CountUp key={key} end={20} duration={5} onEnd={resetAnimation} />
            </VisibilitySensor> / kg
        </h2>
        <h2 className="item-price">
            <img src="https://th.bing.com/th/id/OIP.6g6tXS0XUS5lr6OQ-a-RvgAAAA?rs=1&pid=ImgDetMain" alt="plastic icon" />
            Plastic: ₹<VisibilitySensor>
            <CountUp key={key} end={15} duration={5} onEnd={resetAnimation} />
            </VisibilitySensor> / kg
        </h2>
        <h2 className="item-price">
            <img src="https://cdn1.iconfinder.com/data/icons/elasto-metal-structures-and-products/26/16_i-beam-512.png" alt="metal icon" />
            Metal: ₹<VisibilitySensor>
            <CountUp key={key} end={50} duration={5} onEnd={resetAnimation} />
            </VisibilitySensor> / kg
        </h2>
        <h2 className="item-price">
            <img src="https://th.bing.com/th/id/OIP.Mk90vqFBxX1xq1dvjyWKrwHaHa?pid=ImgDet&w=474&h=474&rs=1" alt="electronics icon" />
            Electronics: As per condition
        </h2>
    </div>
);
```

### Key Points

- **Visibility Sensor**: Ensures that the animation only occurs when the element is visible on the screen.
- **CountUp**: Provides the animated counting effect for prices.
- **Icons**: Visual representation of each scrap material type.

## Component Structure

The `Price` component comprises:

- **Price Heading**: Displays a heading indicating that the best prices are shown.
- **Price Items**: A list of prices for different scrap materials, each with an associated icon and animated count-up effect.

#### CSS Styling

The component uses `price.css` for styling. Ensure to include this CSS file to apply the correct styles.

#### CSS Import

```css
import './price.css';
```

### Handling Errors

- **Visibility Sensor**: Handle cases where the sensor may not work as expected if the element is not properly visible.
- **CountUp**: Handle potential issues with the count-up animation not triggering correctly.

##### Conclusion

The `Price` component provides a visually appealing way to display prices for various scrap materials on a scrap-collecting platform. By using the `CountUp` and `VisibilitySensor` libraries, it ensures that prices are presented in an engaging manner. This documentation should help you integrate and customize the `Price` component for your application.

**File:** `src/components/Price/Price.jsx`

### Blogs

The `Blogs` component is a React component that displays a slider of blog posts. It provides navigation through the blog posts with "Next" and "Previous" buttons and links each blog post to its detailed page. The component employs dynamic styling to create an engaging and interactive carousel effect.

### File Structure

- **Component File**: `Blogs.js`
- **CSS File**: `Blogs.css`
- **Data File**: `BlogsData.json`

## Usage

### Importing the Component

To use the `Blogs` component in your React application, import it as follows:

```jsx
import Blogs from './Blogs';
```

### Example Usage

```jsx
import React from 'react';
import Blogs from './Blogs';

function App() {
    return (
        <div className="App">
            <Blogs />
        </div>
    );
}

export default App;
```

## Component Details

### State Variables

The `Blogs` component uses the `useState` hook to manage its state:

- **active**: Tracks the currently active blog post index in the slider.

```jsx
const [active, setActive] = useState(1);
```

### Blog Slider Logic

The `loadShow` function adjusts the position, opacity, and transformation of blog items to create a carousel effect:

```jsx
const loadShow = () => {
    let stt = 0;
    const items = document.querySelectorAll('.itemBlog');

    // Current active blog styling
    items[active].style.transform = `none`;
    items[active].style.zIndex = 1;
    items[active].style.filter = 'none';
    items[active].style.opacity = 1;

    // Style blogs after the active one
    for (let i = active + 1; i < items.length; i++) {
        stt++;
        items[i].style.transform = `translateX(${120 * stt}px) scale(${1 - 0.2 * stt}) perspective(16px) rotateY(-1deg)`;
        items[i].style.zIndex = -stt;
        items[i].style.filter = 'blur(5px)';
        items[i].style.opacity = stt > 2 ? 0 : 0.6;
    }

    stt = 0;
    // Style blogs before the active one
    for (let i = active - 1; i >= 0; i--) {
        stt++;
        items[i].style.transform = `translateX(${-120 * stt}px) scale(${1 - 0.2 * stt}) perspective(16px) rotateY(1deg)`;
        items[i].style.zIndex = -stt;
        items[i].style.filter = 'blur(5px)';
        items[i].style.opacity = stt > 2 ? 0 : 0.6;
    }
};
```

### Navigation Functions

- **handleNext**: Moves to the next blog post, wraps around to the start if at the end.

```jsx
const handleNext = () => {
    setActive(active + 1 < BlogsData.length ? active + 1 : 0);
    loadShow();
};
```

- **handlePrev**: Moves to the previous blog post, prevents underflow to negative indices.

```jsx
const handlePrev = () => {
    setActive(active - 1 >= 0 ? active - 1 : active);
    loadShow();
};
```

### Blog Items Rendering

The component maps over the `BlogsData` to render each blog post with a "Read More" link that routes to the detailed page of the blog:

```jsx
{BlogsData.map(item => (
    <div key={item.id} className="itemBlog">
        <img src={item.image} alt={`photo-of-${item.title}`} />
        <p>{item.title}</p>
        <a href=""><Link to={`/blogs/${item.id}`}>Read More</Link></a>
    </div>
))}
```

### Return Statement

The return statement provides the JSX structure, including the blog slider and navigation buttons:

```jsx
return (
    <>
        <h1>Blogs</h1>
        <div className="Blogs-main-section">
            <div className="slider">
                {BlogsData.map(item => (
                    <div key={item.id} className="itemBlog">
                        <img src={item.image} alt={`photo-of-${item.title}`} />
                        <p>{item.title}</p>
                        <a href=""><Link to={`/blogs/${item.id}`}>Read More</Link></a>
                    </div>
                ))}
                <button className="next-blog" onClick={handleNext}>&gt;</button>
                <button className="prev-blog" onClick={handlePrev}>&lt;</button>
            </div>
        </div>
    </>
);
```

## Component Structure

The `Blogs` component comprises:

- **Blog Header**: Displays a header for the blogs section.
- **Blog Slider**: A container for the blog items, styled to act as a carousel.
- **Navigation Buttons**: Buttons to navigate through the blogs.

#### CSS Styling

The component uses `Blogs.css` for styling. Ensure to include this CSS file to apply the correct styles.

#### CSS Import

```css
import './Blogs.css';
```
### Handling Errors

- **Navigation Bounds**: Ensure the active index does not exceed the bounds of the `BlogsData` array.
- **QuerySelector**: Ensure that `document.querySelectorAll` correctly selects the blog items.

#### Conclusion

The `Blogs` component provides a visually appealing and interactive way to showcase blog posts on a website. It features a carousel with dynamic transformations and opacity changes to highlight the active blog post. This documentation should help you integrate and customize the `Blogs` component for your application.

**File:** `src/components/Blogs/Blogs.jsx`

## Routing

The application uses `react-router-dom` for routing. Below are the defined routes:

- `/` - Loads the `Master` component.
- `/form` - Loads the `Form` component for listing scrap items.
- `/price` - Displays the `Price` component with real-time scrap rates.
- `/done` - Shows the `Done` component confirming a successful listing.
- `/blogs/:id` - Displays a specific blog post through the `BlogDetails` component.
- `/order` - Shows the `Order` component for vendors to manage orders.
- `/Blogs` - Lists all the blogs through the `Blogs` component.

## Contributing

We welcome contributions to enhance the platform. To contribute, follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bugfix:
   ```bash
   git checkout -b feature-name
   ```
3. Make your changes and commit them:
   ```bash
   git commit -m "Add feature name"
   ```
4. Push to the branch:
   ```bash
   git push origin feature-name
   ```
5. Open a pull request.

## License

## MIT License

**Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:**

1. **Attribution**:
   - The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
   
2. **Modification**:
   - You are free to modify the Software for your own use or for distribution.

3. **Distribution**:
   - You can distribute copies of the Software, either as-is or modified, under the same license terms.

4. **Commercial Use**:
   - The Software can be used for commercial purposes without any restrictions.

5. **Sublicensing**:
   - You are permitted to sublicense the Software, meaning you can grant rights to the Software to other parties.

6. **Warranty Disclaimer**:
   - THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

7. **Limitation of Liability**:
   - In no event shall the authors or copyright holders be liable for any claim, damages, or other liability arising from the use of the Software.

8. **Termination**:
   - The license and rights granted under it are perpetual, meaning they last forever, unless you violate any of the conditions above.

9. **Patent Rights**:
   - No patent rights are granted under this license.

---

### License Summary

This project is licensed under the MIT License. You are free to use, copy, modify, and distribute this software for any purpose, including commercial applications, under the following conditions:

- You must include the original copyright notice and this permission notice in any copies of the software.
- The software is provided "as is", without warranty of any kind.

---

### Attribution

When using or redistributing this code, you must include the following attribution:

```
Created by [utsavmehta24]
```

---

### Frequently Asked Questions

1. **Can I use this project for commercial purposes?**
   - Yes, you can use this project for commercial purposes.

2. **Can I modify the code?**
   - Yes, you are free to modify the code.

3. **Do I have to release my modifications?**
   - No, you are not required to release your modifications, but if you distribute them, they must be under the same MIT License.

4. **Do I need to include the original license in my distributed code?**
   - Yes, you must include the original copyright notice and this license in any copies of the software.

5. **Is there any warranty for the software?**
   - No, the software is provided "as is", without any warranty.

---

Thank you for using and contributing to the Scrap Platform! If you have any questions or feedback, please open an issue or reach out to us.
#
#   E c o - R a d d i  
 