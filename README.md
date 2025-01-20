# node-fetch-api
Learn how to make HTTP requests in Node.js using the Node-Fetch API, and discover how to integrate Scrapeless's powerful Scraping Toolkit.
## How to Make HTTP Requests in Node.js with Node-Fetch API
Our current websites usually rely on dozens of different resources, such as a monolithic collection of images, CSS, fonts, JavaScript, JSON data, etc. However, the world's first website was written only in HTML.

JavaScript, as an excellent client-side scripting language, has played an important role in the evolution of websites. With the help of XMLHttpRequest or XHR objects, JavaScript can achieve communication between clients and servers without reloading the page.

However, this dynamic process is challenged by Fetch API. What is Fetch API? How to use Fetch API in Node.js? Why is Fetch API a better choice?

Start getting answers from this article now!

## What Are HTTP Requests in Node.js?
In Node.js, HTTP requests are a fundamental part of building web applications or interacting with web services. They allow a client (like a browser or another application) to send data to a server, or request data from a server. These requests use the Hypertext Transfer Protocol (HTTP), which is the foundation of data communication on the web.
1. **HTTP Request**: An HTTP request is sent by a client to a server, typically to retrieve data (like a webpage or API response) or to send data to the server (like submitting a form).
2. **HTTP Methods**: HTTP requests usually include a method, which indicates what action the client wants the server to take. Common HTTP methods include:
  - **GET**: Request data from the server.
  - **POST**: Send data to the server (e.g., submitting a form).
  - **PUT**: Update existing data on the server.
  - **DELETE**: Remove data from the server.
3. **Node.js HTTP Module**: Node.js provides a built-in http module to handle HTTP requests. This module enables you to create an HTTP server, listen for requests, and respond to them.

### Why Node.js is ideal for web scraping and automation?
Node.js has become one of the go-to technologies for web scraping and automation tasks due to its unique characteristics, robust ecosystem, and asynchronous, non-blocking architecture.

Why Node.js is ideal for web scraping and automation? Let's figure them out!
1. Asynchronous and non-blocking I/O
2. Speed and efficiency
3. Rich ecosystem of libraries and frameworks
4. Handling of dynamic content with headless browsers
5. Cross-platform compatibility
6. Real-time data processing
7. Simple syntax for rapid development
8. Support for proxy rotation and anti-detection

### What is Node-Fetch API?
Node-fetch is a lightweight module that brings the Fetch API to the Node.js environment. It simplifies the process of making HTTP requests and handling responses.

The Fetch API is built around Promises and is well suited for asynchronous operations such as scraping data from a website, interacting with a RESTful API, or automating tasks.

## How to use Fetch API in Node.JS?
The Fetch API is a modern, Promise-based interface designed to handle network requests in a more efficient and flexible manner compared to the traditional XMLHttpRequest object.

It is natively supported in contemporary browsers, meaning there is no need for additional libraries or plugins. In this guide, we will explore how to utilize the Fetch API to perform GET and POST requests, as well as how to manage responses and errors effectively.

> 💬 **Note**: If Node.js is not installed on your computer, you need to install it first. You can download the Node.js installation package suitable for your operating system [here](https://nodejs.org/en/download/). The recommended Node.js version is 18 and above.

### Step 1. Initialize your Node.js project
If you haven't created a project yet, you can create a new project with the following command:

```Bash
mkdir fetch-api-tutorial
cd fetch-api-tutorial
npm init -y
```
Open the package.json file, add the type field, and set it to module:

```JSON
{
  "name": "fetch-api-tutorial",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "type": "module",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

### Step 2. Download and install the `node-fetch` library
This is a library for using the Fetch API in Node.js. You can install the `node-fetch` library with the following command:

```Bash
npm install node-fetch
```

After the download is complete, we can start using the Fetch API to send network requests. Create a new file index.js in the root directory of the project and add the following code:

```JavaScript
import fetch from 'node-fetch';

fetch('https://jsonplaceholder.typicode.com/posts')
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

Execute the following command to run the code:

```Bash
node index.js
```

We will see the following output:

![output](https://assets.scrapeless.com/prod/posts/node-fetch-api/0f4b80e83f09bcda1a89f9de48a342f9.png)

### Step 3. Use Fetch API to send POST request
How to use Fetch API to send the `POST` request? Please refer to the following method. Create a new file `post.js` in the root directory of the project and add the following code:
```JavaScript
import fetch from 'node-fetch';

const postData = {
  title: 'foo',
  body: 'bar',
  userId: 1,
};

fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify(postData),
})
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

Let's analyze this code:
- We first define an object called `postData`, which contains the data we want to send.
- Then we use the `fetch` function to send a POST request to `https://jsonplaceholder.typicode.com/posts`, passing a configuration object as the second parameter.
- The configuration object contains the request `method`, request `headers`, and request `body`.

Execute the following command to run the code:

```Bash
node post.js
```

The output you can see:

![output](https://assets.scrapeless.com/prod/posts/node-fetch-api/8e0e72403bf7f16bcb30e98ffa74d2c5.png)

### Step 4. Handling Fetch API response results and errors
We need to create a new file `response.js` in the root directory of the project and add the following code:

```JavaScript
import fetch from 'node-fetch';

fetch('https://jsonplaceholder.typicode.com/posts-response')
  .then((response) => {
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    return response.json();
  })
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

In the above code, we first fill in an incorrect URL address to trigger an HTTP error. Then we check the status code of the resulting response in the then method, and throw an error if the status code is not 200. Finally, we catch the error in the `catch` method and print it out.

Execute the following command to run the code:

```Bash
node response.js
```

After the code is executed, you will see the following output:

![output](https://assets.scrapeless.com/prod/posts/node-fetch-api/a1ebb67ee5a81605fd43d612b8e875b0.png)

## 3 Common Challenges in Web Scraping
### 1. CAPTCHAs
CAPTCHAs (Completely Automated Public Turing tests to tell Computers and Humans Apart) are designed to prevent automated systems, like web scrapers, from accessing websites. They typically require users to prove they are human by solving puzzles, identifying objects in images, or entering distorted characters.

### 2. Dynamic content
Many modern websites use JavaScript frameworks like React, Angular, or Vue.js to load content dynamically. This means that the content you see in the browser is often rendered after the page loads, making it difficult to scrape with traditional methods that rely on static HTML.

### 3. IP bans
Websites often implement measures to detect and block scraping activities, one of the most common methods being IP blocking. This occurs when too many requests are sent from the same IP address in a short period, causing the website to flag and block that IP.

## Scrapeless Scraping Toolkit - Efficient Scraping Tool
Scrapeless is one of the [**best comprehensive scraping tools**](https://www.scrapeless.com/en) due to its ability to bypass website blocks in real time, including IP blocking, CAPTCHA challenges, and JavaScript rendering. It supports advanced features like IP rotation, TLS fingerprint management, and CAPTCHA solving, making it ideal for large-scale web scraping.

### How Scrapeless enhances Node.js web scraping projects?
Its easy integration with Node.js and high success rate for avoiding detection make Scrapeless a reliable and efficient choice for bypassing modern anti-bot defenses, ensuring smooth and uninterrupted scraping operations.

### Advantages of using a scraping toolkit like Scrapeless over manual scraping
1. Efficient handling of website blocks: Scrapeless can bypass common anti-scraping defenses like **IP blocks, CAPTCHAs, and JavaScript rendering** in real time, which manual scraping cannot handle efficiently.
2. Reliability and success rate: Scrapeless uses advanced features like **IP rotation and TLS fingerprint management** to avoid detection, ensuring a higher success rate and uninterrupted scraping compared to manual scraping.
3. Easy Integration and Automation: Integrates seamlessly with **Node.js** and automates the entire scraping workflow, which saves time and reduces human error compared to manual data collection.

Just follow some easy steps, you can integrate Scrapeless into your Node.js project.

It's time to keep scrolling! The following will be more wonderful!

## Integrating Scrapeless Scraping Toolkit into Your Node.js Project
Before you get started, you need to [**register a Scrapeless account**](https://app.scrapeless.com/passport/register?utm_source=official&utm_medium=blog&utm_campaign=node-fetch-api). You can also refer to the [official website](https://www.scrapeless.com/) to learn more about Scrapeless.

### Step 1. Access Scrapeless Scraping API in Node.js
We need to go to the Scrapeless [Dashboard](https://app.scrapeless.com/passport/register?utm_source=official&utm_medium=blog&utm_campaign=node-fetch-api), click the "**Scraping API**" menu on the left, and then select a service you want to use.

Here we can use the "**Amazon**" service

![Amazon api](https://assets.scrapeless.com/prod/posts/node-fetch-api/52dd053034d49804f748527103b324f4.png)

Entering the Amazon API page, we can see that Scrapeless has provided us with default parameters and code examples in three languages:
- **Python**
- **Go**
- **Node.js**

Here we choose Node.js and copy the code example to our project:

![Node.js](https://assets.scrapeless.com/prod/posts/node-fetch-api/7c47658a1d26112d9701e9d0ba848b9e.png)

The Node.js code examples of Scrapeless use the `http` module by default. We can use the `node-fetch` module to replace the http module, so that we can use the Fetch API to send network requests.

First, create a `scraping-api-amazon.js` file in our project, and then replace the code examples provided by Scrapeless with the following code examples:

```JavaScript
import fetch from 'node-fetch';

class Payload {
  constructor(actor, input) {
    this.actor = actor;
    this.input = input;
  }
}

async function sendRequest() {
  const host = 'api.scrapeless.com';
  const url = `https://${host}/api/v1/scraper/request`;
  const token = ''; // Your API token

  const inputData = {
    action: 'product',
    url: 'https://www.amazon.com/dp/B0BQXHK363',
  };

  const payload = new Payload('scraper.amazon', inputData);

  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'x-api-token': token,
      },
      body: JSON.stringify(payload),
    });

    if (!response.ok) {
      throw new Error(`HTTP Error: ${response.status}`);
    }

    const body = await response.text();
    console.log('body', body);
  } catch (error) {
    console.error('Error:', error);
  }
}

sendRequest();
```

Run the code by executing the following command:

```Bash
node scraping-api-amazon.js 
```

We will see the results returned by the Scrapeless API. Here we simply print them out. You can process the returned results according to your needs.

![returned results](https://assets.scrapeless.com/prod/posts/node-fetch-api/189c0d7e595e940e416ac98236114500.png)

### Step 2. Leveraging Web Unlocker for Bypassing Common Anti-Scraping Measures

Scrapeless provides a **Web unlocker** service that can help you bypass common anti-scraping measures, such as CAPTCHA bypass, IP blocking, etc. The Web unlocker service can help you solve some common crawling problems and make your crawling tasks smoother.

To verify the effectiveness of the Web unlocker service, we can first use the curl command to access a website that requires a CAPTCHA, and then use the Scrapeless Web unlocker service to access the same website to see if the CAPTCHA can be successfully bypassed.

1. Use the curl command to access a website that requires a verification code, such as `https://identity.getpostman.com/login`：

```Bash
curl https://identity.getpostman.com/login
```

By looking at the returned results, we can see that this website is connected to `Cloudflare` verification mechanism, and we need to enter the verification code to continue accessing the website.

![Cloudflare verification mechanism](https://assets.scrapeless.com/prod/posts/node-fetch-api/32eb99ee81850cb13b8280eda9c39cef.png)

2. We use Scrapeless Web unlocker service to access the same website:
- Go to [**Scrapeless Dashboard**](https://app.scrapeless.com/passport?utm_source=official&utm_medium=blog&utm_campaign=node-fetch-api)
- **Click the Web unlocker menu on the left**

![Click the Web unlocker](https://assets.scrapeless.com/prod/posts/node-fetch-api/b74fb6e1a159529bfd4c7ec789195213.png)

- **Copy the Node.js code example to our project**

Here we create a new `web-unlocker.js` file. We still need to use the node-fetch module to send network requests, so we need to replace the http module in the code example provided by Scrapeless with the node-fetch module:

```JavaScript
import fetch from 'node-fetch';

class Payload {
  constructor(actor, input, proxy) {
    this.actor = actor;
    this.input = input;
    this.proxy = proxy;
  }
}

async function sendRequest() {
  const host = 'api.scrapeless.com';
  const url = `https://${host}/api/v1/unlocker/request`;
  const token = ''; // Your API token

  const inputData = {
    url: 'https://identity.getpostman.com/login',
    method: 'GET',
    redirect: false,
  };

  const proxy = {
    country: 'ANY',
  };

  const payload = new Payload('unlocker.webunlocker', inputData, proxy);

  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'x-api-token': token,
      },
      body: JSON.stringify(payload),
    });

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const body = await response.text();
    console.log('body', body);
  } catch (error) {
    console.error('Error:', error);
  }
}

sendRequest();
```

Execute the following command to run the script:

```JavaScript
web-unlocker.js
```
![run the script](https://assets.scrapeless.com/prod/posts/node-fetch-api/302bf853f78cf1ffba2e6e421bf087f5.png)

![Scrapeless Web unlocker successfully bypassed CAPTCHA](https://assets.scrapeless.com/prod/posts/node-fetch-api/e3147fc99461bc1505f144a72e77d5f6.png)


Look! Scrapeless Web unlocker successfully bypassed the verification code, and we can see that the returned results contain the web page content we need.

## FAQs
### Q1. Node-Fetch vs Axios: which is better for web scraping?
To make your choice easier, Axios and Fetch API have the following differences:
1. Fetch API uses the body property of the request, while Axios uses the data property.
2. With Axios, you can send JSON data directly, while Fetch API needs to be converted to a string.
3. Axios can process JSON directly. Fetch API requires calling the response.json() method first to get a response in JSON format.
4. For Axios, the response data variable name must be data; for Fetch API, the response data variable name can be anything.
5. Axios allows easy monitoring and updating of progress using progress events. There is no direct method in Fetch API.
6. Fetch API does not support interceptors, while Axios does.
7. Fetch API allows streaming responses, while Axios does not.

### Q2. Is node fetch stable?
The most notable feature of Node. js v21 is the stabilization of the Fetch API.

### Q3. Is Fetch API better than AJAX?
For new projects, it's recommended to use the Fetch API due to its modern features and simplicity. However, if you need to support very old browsers or are maintaining legacy code, Ajax might still be necessary.

## The Bottom Lines
The addition of Fetch API in Node.js is a long-awaited feature. Using Fetch API in Node.js can ensure that your scraping work is done easily. However, it is inevitable to encounter serious network blockades when using Node Fetch API.

Want to completely solve IP bans and CAPTCHA? **Be sure to use [Scrapeless](https://app.scrapeless.com/passport/register?utm_source=official&utm_medium=blog&utm_campaign=node-fetch-api) to easily bypass website monitoring and IP blocking.**
