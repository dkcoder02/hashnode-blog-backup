---
title: "What is CSR SSR SSG and ISR"
seoTitle: "Understanding SSR, CSR, ISR, and SSG"
seoDescription: "Explore the different rendering techniques in Next.js, including CSR, SSR, SSG, and ISR, for better performance and user experience"
datePublished: Sun Mar 09 2025 11:13:27 GMT+0000 (Coordinated Universal Time)
cuid: cm81jbzll000207jv24nh9nxg
slug: what-is-csr-ssr-ssg-and-isr
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1741515022426/0ae5144a-debb-495f-b65e-5b90d48e7425.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1741518545754/6a4a68c9-70ac-498a-ae58-e0c33ec6e81b.png

---

In Next.js, different rendering techniques impact performance and user experience. This post will cover *Client Side Rendering (CSR), Server Side Rendering (SSR), Static Site Generation (SSG), and Incremental Static Regeneration (ISR)*

---

## The Build Process

Before diving into the specifics of each rendering technique, it's important to understand the basic build process

1. ***Source Code* :** This is the code written in JavaScript files
    
2. ***Build Phase* :** During the build phase, the source code is processed and optimized. This is when commands like `npm run build` are executed
    
3. ***Server* :** The built files are stored on a server, which could be **Vercel, Netlify, or a Static** server
    
4. ***Client* :** The client, such as a web browser, requests and receives web pages from the server
    

---

## Client Side Rendering (CSR)

With Client-Side Rendering (CSR), the majority of the work is done on the client-side

* The server sends an **empty HTML page** to the client
    
* The server also sends JavaScript files
    
* The client's browser then executes the JavaScript code to render the web page
    
* The entire web page is built on the client side
    
* If more JavaScript or CSS is needed, the client requests it from the server
    

While CSR can provide a Dynamic User Experience, it has some Drawbacks:

* **Poor Search Engine Optimization (SEO) :** Since the initial HTML is empty, search engines have nothing to crawl, which hurts SEO
    
* **Initial Load Time :** Users may experience a delay while the JavaScript is downloaded and executed
    

*CSR is suitable* for web applications like *SaaS dashboards* where SEO is not a primary concern

```javascript
// App Router Example

'use client';  // This Flag used to render page on client-side

import { useEffect, useState } from "react";

export default function Page() {
    const [stockData, setStockData] = useState([]);

    const apiCall= async () => {
        const data = await fetch('https://api.freeapi.app/api/v1/public/stocks?page=1&limit=2&inc=Symbol%2CName%2CMarketCap%2CCurrentPrice&query=tata')
        const result= await data.json()
        setStockData(result?.data?.data || [])
    }

    useEffect(() => {
        apiCall()
    }, [])

    return (
        <>
            <h1>CSR Example</h1>
            <ul>
                {stockData.map((stock) => (
                    <li key={stock.id}>{stock.Name}</li>
                ))}
            </ul>
        </>
    )
}
```

## **Server-Side Rendering (SSR)**

In Server-Side Rendering (SSR), the rendering process happens on the server

* When the client makes a request, the server retrieves the necessary data
    
* The server then renders the web page and sends the complete HTML to the client
    
* Every time the client requests a new page, the server repeats the process
    

---

### SSR offers several advantages :

1. **Improved SEO :** Search engines can crawl the fully rendered HTML, leading to better SEO
    
2. **Faster Initial Load Time :** The client receives a fully rendered page, improving the initial load time
    

However, SSR also has some drawbacks :

* **Server Load :** The server has to render the page for every request, which can increase server load
    
* **Time Consumption :** Although the server has more computing power, the rendering process still takes time
    

```javascript
// App Router Example

export default async function Page() {
    const data = await fetch('https://api.vercel.app/blog')
    const posts = await data.json()   
 
    return (
        <ul>
            {posts.map((post: any) => (
                <li key={post.id}>{post.title}</li>
            ))}
        </ul>
    )
}
```

---

## **Static Site Generation (SSG)**

Static Site Generation (SSG) generates web pages at build time

* During the build process, each page is rendered and saved as static HTML files.
    
* These pre-rendered pages are then stored on the server.
    
* When a client requests a page, the server simply sends the corresponding HTML file.
    

SSG offers significant performance benefits :

* **Fast Loading Times :** Since the pages are pre-rendered, they load very quickly.
    
* **Reduced Server Load :** The server only needs to serve static files, which reduces server load.
    
* **Improved SEO :** Static Site Generation (SSG) improves SEO because search engines can easily crawl the static HTML files. These files are pre-rendered and stored on the server, allowing search engines to access and index the content efficiently, which enhances visibility and ranking in search results.
    

SSG is ideal for websites with content that **doesn't change frequently**, such as **Blogs or documentation** sites. However, *it may not be suitable for sites with frequently updating content.*

---

## Incremental Static Regeneration (ISR)

Incremental Static Regeneration (ISR) is a **hybrid approach** that combines the benefits of **SSG and SSR.**

* Like SSG (**Static Site Generation)**, ISR generates static pages at build time.
    
* However, ISR also allows you to **re-generate pages** in the background at specified intervals.
    
* This ensures that the content is updated regularly without sacrificing performance.
    

ISR offers a balance between Performance and Content Freshness :

* **Updated Content :** Content can be updated at specified intervals.
    
* **Performance :** Because it leverages static generation, it still delivers great performance.
    

ISR is suitable for websites where content updates periodically.

---

## **Choosing the Right Approach**

Selecting the right rendering technique depends on the specific needs of your project.

1. **Build Time :** How important is build time ?.
    
2. **Dynamic Content :** How often does the content get updated ?.
    
3. **SEO :** How valuable is search engine optimization ?.
    
4. **Rendering Time :** Is build time or server-client time more important ?.
    
5. **Content Update :** How often do you want your content to update ?.
    

*There is no one-size-fits-all solution. Each technique has its own trade-offs, and the best choice depends on the specific requirements of your website or application.*

---

## Conclusion

In conclusion, understanding the different rendering techniques in Next.js Client-Side Rendering (CSR), Server-Side Rendering (SSR), Static Site Generation (SSG), and Incremental Static Regeneration (ISR) is crucial for optimizing performance and user experience

If you found this blog post helpful, please consider sharing it with others who might benefit. You can also follow me for more content on JavaScript, React.js, Next.js, and other web Development topics.

For *Paid collaboration*, *Web Development freelancing* *work*, mail me at: [**krishdesai044@gmail.com**](mailto:krishdesai044@gmail.com)

Connect with me on [**Twitter**](https://x.com/DKB972), [**LinkedIn**](https://www.linkedin.com/in/krishdesai117/), and [**GitHub**](https://github.com/dkcoder02).

Thank you for Reading

Happy Coding