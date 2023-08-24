# 404-redirect
A new technique that use 404 pages for redirecting and site-building.

## What is it?
Nowadays, website redirect (*aka.* short-url) is widely used for many purposes. For example, when you type `aka.ms/vscode`, you will be redirected to `https://code.visualstudio.com/`. This is a common way to shorten the URL.

However, the logic behind the short-url is not that simple. It requires a server to do the mapping.

For some developers, they may want to have a short-url but don't want to build a server for it. In this case, they can use the 404 page to do the redirecting.

> When you visit a page that doesn't exist, the server will return a 404 page. This page **won't change the URL in the browser**. Therefore, we can use this page to do the redirecting.

With this technique, you can build your own short-url service without a new server! And more, you can even build a website with it! (see [*OpenTeens.org*](openteens.org) for an example)

## How to use it?
The simplest way is to use the example code in this repo, or you can follow the steps below to write your own:

1. Create a 404 page in your website. For example, `https://example.com/404.html`.

2. Get the request URL in the 404 page. For example, in the `404.html` page, you can use the following code to get the request URL:
    ```js
    var url = window.location.href;
    ```
    > You can also use other methods to get the request URL. For example, in PHP, you can use `$_SERVER['REQUEST_URI']`.

3. Do the mapping and redirecting. For example, you can use the following code to redirect the request:
    ```js
    var mapping = {
        'vscode': 'https://code.visualstudio.com/',
        'azure': 'https://azure.microsoft.com/',
        'github': '...'
    };
    var redirectUrl = mapping[url]; // map
    window.location.href = redirectUrl; // redirect
    ```

## Examples in this repo
This repo provides two following examples:

1. 404-redirect
    at `examples/404-redirect/`

    A simple example that shows the basic idea of 404-redirect, and do the basic steps mentioned above.

2. 404-website
    at `examples/404-website/`

    A website example the build with 404-redirect. You can use this example to build your own website!

For a more complex example, you can visit [OpenTeens.org](openteens.org) to see how it works.
