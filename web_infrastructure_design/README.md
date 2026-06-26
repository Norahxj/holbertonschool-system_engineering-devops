# 0. Simple Web Stack

![Simple Web Stack Diagram](./images/simple_web_stack.png)

## Explanation

A user wants to access the website `www.foobar.com` from their computer. The user types the domain name into the browser. The browser asks DNS to resolve `www.foobar.com` into an IP address. The DNS record points `www.foobar.com` to the server IP address `8.8.8.8`. Then the browser sends a request to the server using the Internet, mainly through the HTTP or HTTPS protocol over TCP/IP.

The infrastructure contains one server. A server is a physical or virtual machine that provides services to other computers over a network. In this case, the server hosts the whole website infrastructure.

The domain name is `foobar.com`. The role of the domain name is to give users a human-readable name instead of asking them to remember the server IP address. The `www` in `www.foobar.com` is a subdomain. In this task, it is configured as a DNS record that points to the server IP `8.8.8.8`. The DNS record type is an **A record** because it maps a hostname to an IPv4 address.

Inside the server, there is a web server, which is **Nginx**. The role of Nginx is to receive HTTP or HTTPS requests from the user’s browser. It can serve static files directly, such as HTML, CSS, JavaScript, and images. It can also forward dynamic requests to the application server.

The application server runs the backend logic of the website. It executes the application code and processes requests that need business logic, such as login, forms, user accounts, or dynamic pages.

The application files are the website’s code base. They contain the source code used by the application server to generate the website’s dynamic content.

The database is **MySQL**. Its role is to store and manage the website’s data, such as users, posts, products, sessions, or any other persistent information needed by the application.

The server communicates with the user’s computer using network protocols. The main communication uses **HTTP or HTTPS** for web requests, running on top of **TCP/IP**.

## Issues with this Infrastructure

This infrastructure has several problems.

First, it has a **SPOF**, which means **Single Point of Failure**. Since everything is hosted on one server, if that server goes down, the whole website becomes unavailable. The web server, application server, application files, and database are all on the same machine, so one failure can stop the entire website.

Second, there can be downtime during maintenance. For example, if we need to deploy new code or restart Nginx or the application server, the website may become temporarily unavailable because there is no second server to continue serving traffic.

Third, this infrastructure cannot scale well if there is too much incoming traffic. Since there is only one server, all requests go to the same machine. If traffic increases too much, the server can become overloaded in CPU, memory, disk, or network usage, causing the website to become slow or unavailable.
