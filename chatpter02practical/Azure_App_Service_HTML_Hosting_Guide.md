# Hosting a Simple HTML Page on Azure App Service

## 1. Objective

Host a simple HTML website on **Microsoft Azure App Service** and access it through a public Azure URL.

The overall flow is:

```text
HTML Page
    ↓
Azure App Service
    ↓
Public URL
    ↓
Browser
```

Example URL:

```text
https://your-app-name.azurewebsites.net
```

---

# 2. Prerequisites

Before starting, make sure you have:

- A Microsoft/Azure account
- An active Azure subscription
- Internet connection
- A Windows/Linux/macOS computer
- A text editor such as VS Code or Notepad
- A simple HTML file

Open the Azure Portal:

https://portal.azure.com/

---

# 3. Create the HTML Project Locally

Create a folder on your computer.

Example:

```text
C:\rungta\azure-app-service\html-demo
```

Inside the folder create:

```text
html-demo
│
└── index.html
```

---

# 4. Create `index.html`

Open `index.html` in VS Code or Notepad.

Use the following code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Azure App Service Demo</title>
</head>
<body>

    <h1>Welcome to Azure App Service</h1>

    <p>This HTML page is hosted using Microsoft Azure App Service.</p>

    <h2>My First Azure Web App</h2>

</body>
</html>
```

Save the file.

---

# 5. Test the HTML Page Locally

Before uploading the website to Azure, test it locally.

Double-click:

```text
index.html
```

It should open in your browser.

You should see:

```text
Welcome to Azure App Service

This HTML page is hosted using Microsoft Azure App Service.

My First Azure Web App
```

If it works locally, continue with Azure deployment.

---

# 6. Create a Resource Group

A **Resource Group** is a logical container used to organize Azure resources.

For this practical, create:

```text
rg-html-demo
```

## Steps

1. Open:

   https://portal.azure.com/

2. Search for:

```text
Resource groups
```

3. Open **Resource groups**.

4. Click:

```text
+ Create
```

5. Select your Azure subscription.

6. Enter the Resource Group name:

```text
rg-html-demo
```

7. Select a region.

Example:

```text
Central India
```

8. Click:

```text
Review + create
```

9. After validation succeeds, click:

```text
Create
```

---

# 7. Create an Azure App Service

Now create the actual web hosting service.

## Steps

1. In Azure Portal, search for:

```text
App Services
```

2. Open **App Services**.

3. Click:

```text
+ Create
```

4. Select:

```text
Web App
```

---

# 8. Configure the Web App

The Web App creation page contains several sections.

## 8.1 Subscription

Select your Azure subscription.

Example:

```text
Azure for Students
```

Use the subscription that is available in your account.

---

# 9. Select the Resource Group

Select the Resource Group created earlier:

```text
rg-html-demo
```

---

# 10. Enter the Web App Name

Enter a globally unique name.

Example:

```text
ashutosh-html-demo-2026
```

The name must be unique because it becomes part of the public Azure hostname.

For example:

```text
https://ashutosh-html-demo-2026.azurewebsites.net
```

If the name is already taken, use another name:

```text
ashutosh-html-demo-2026-01
```

or:

```text
ashutosh-web-demo-2026
```

---

# 11. Select the Deployment Type

For this practical, select:

```text
Publish: Code
```

We are deploying HTML files rather than a Docker container.

---

# 12. Select the Runtime Stack

A pure HTML website does not require an application framework.

Azure App Service requires a supported application runtime/environment, and the exact choices can change in the Azure Portal.

For a simple static HTML demonstration, select a currently supported web runtime available in the portal.

For example, if PHP is available:

```text
Runtime stack: PHP
```

The HTML files themselves do not require PHP code.

---

# 13. Select the Operating System

Select:

```text
Linux
```

---

# 14. Select the Region

Select a suitable Azure region.

For example:

```text
Central India
```

You can use another region if it is more appropriate for your users or subscription.

---

# 15. Configure the App Service Plan

An **App Service Plan** provides the compute resources used by your Web App.

Conceptually:

```text
App Service Plan
│
├── CPU
├── Memory
└── Pricing Tier
```

The Web App runs inside the App Service Plan.

If Azure asks you to create a new plan, give it a name such as:

```text
ASP-html-demo
```

---

# 16. Select the Pricing Tier

Click:

```text
Change size
```

or:

```text
Explore pricing plans
```

Depending on the current Azure Portal interface.

For a classroom demonstration or learning project, select an appropriate low-cost/free tier if one is available to your subscription.

Possible tiers can include:

```text
Free
Shared
Basic
Standard
Premium
```

The exact plans and availability can change over time.

For a simple HTML demonstration, a high-performance production tier is unnecessary.

---

# 17. Understand App Service and App Service Plan

These two concepts are different.

## App Service

This is your actual web application.

Example:

```text
ashutosh-html-demo-2026
```

## App Service Plan

This provides the compute environment.

Example:

```text
ASP-html-demo
```

Relationship:

```text
App Service Plan
        ↓
   App Service
        ↓
   Web Application
        ↓
     index.html
```

---

# 18. Review the Configuration

Before creating the App Service, verify the important settings.

```text
Subscription       → Your Azure subscription
Resource Group     → rg-html-demo
Web App Name       → Unique name
Publish            → Code
Runtime            → Supported runtime
Operating System   → Linux
Region             → Selected region
App Service Plan   → ASP-html-demo
Pricing Tier       → Selected tier
```

Click:

```text
Review + create
```

Azure will validate the configuration.

If validation succeeds, click:

```text
Create
```

---

# 19. Wait for Deployment

Azure will display deployment progress.

Wait until the deployment finishes.

You should eventually see that the deployment has completed.

Click:

```text
Go to resource
```

You are now inside your Azure App Service.

---

# 20. Find the Default Domain

On the App Service **Overview** page, find:

```text
Default domain
```

It will look similar to:

```text
https://your-app-name.azurewebsites.net
```

For example:

```text
https://ashutosh-html-demo-2026.azurewebsites.net
```

Open the URL in your browser.

At this point, you may see the Azure default page.

That is normal because your `index.html` has not been deployed yet.

---

# 21. Deploy the HTML File

There are multiple ways to deploy files to Azure App Service.

Common methods include:

1. ZIP deployment
2. Visual Studio Code / Azure extension
3. GitHub deployment
4. Azure DevOps deployment
5. Other supported deployment mechanisms

For this beginner practical, ZIP deployment is a useful method to understand.

---

# 22. Prepare the Website ZIP File

Your local project should look like:

```text
html-demo
│
└── index.html
```

Create a ZIP file containing the website files.

The important structure is:

```text
index.zip
│
└── index.html
```

Avoid accidentally creating:

```text
index.zip
│
└── html-demo
    │
    └── index.html
```

The application files should be packaged at the appropriate deployment root.

---

# 23. Open Advanced Tools

Return to your Azure App Service.

In the left-hand menu, find:

```text
Advanced Tools
```

Open it.

Click:

```text
Go
```

This opens the App Service management environment commonly known as **Kudu**.

The URL may look similar to:

```text
https://your-app-name.scm.azurewebsites.net
```

---

# 24. Open the Debug Console

Inside the Kudu environment, open:

```text
Debug console
```

Depending on the environment, you may see:

```text
CMD
```

or:

```text
Bash
```

Choose the available shell.

---

# 25. Understand the `wwwroot` Directory

For a Linux App Service, the application content is commonly located under:

```text
/home/site/wwwroot
```

Think of the structure as:

```text
App Service
    │
    └── /home/site/wwwroot
            │
            └── index.html
```

The web application's files need to be deployed into the appropriate application root.

---

# 26. Verify the Application Directory

In a Linux shell, you can use:

```bash
cd /home/site/wwwroot
```

Then:

```bash
ls
```

You should be able to see your deployed files.

For example:

```text
index.html
```

---

# 27. Deploy `index.html`

Upload/deploy:

```text
index.html
```

to:

```text
/home/site/wwwroot
```

The final structure should be:

```text
/home/site/wwwroot
│
└── index.html
```

---

# 28. Verify `index.html`

Run:

```bash
cd /home/site/wwwroot
```

Then:

```bash
ls
```

You should see:

```text
index.html
```

You can also inspect the file using available shell commands.

For example:

```bash
cat index.html
```

This displays the contents of the HTML file.

---

# 29. Open the Website

Go back to:

```text
Azure Portal
    ↓
App Service
    ↓
Overview
```

Copy the:

```text
Default domain
```

For example:

```text
https://ashutosh-html-demo-2026.azurewebsites.net
```

Open it in your browser.

Your HTML page should now appear.

---

# 30. Complete Architecture

The complete architecture is:

```text
                    INTERNET
                        │
                        ▼
                Browser / Client
                        │
                        │ HTTPS
                        ▼
             Azure App Service URL
                        │
                        ▼
               Azure App Service
                        │
                        ▼
                   Web Server
                        │
                        ▼
              /home/site/wwwroot
                        │
                        ▼
                    index.html
```

---

# 31. How the Request Works

Suppose your website URL is:

```text
https://ashutosh-html-demo-2026.azurewebsites.net
```

When a user opens it:

### Step 1

The browser sends an HTTPS request.

```text
Browser
   ↓
Azure URL
```

### Step 2

DNS resolves the Azure hostname.

### Step 3

The request reaches Azure App Service.

### Step 4

The App Service web environment processes the request.

### Step 5

The default document is located.

For this website:

```text
index.html
```

### Step 6

Azure sends the HTML response back to the browser.

### Step 7

The browser renders the webpage.

---

# 32. Understanding `wwwroot`

The `wwwroot` directory is an important concept.

A website can contain:

```text
wwwroot
│
├── index.html
├── about.html
├── contact.html
├── css
│   └── style.css
└── images
    └── logo.png
```

The files are served as part of the web application.

For example:

```text
/                 → index.html
/about.html       → about.html
/contact.html     → contact.html
```

---

# 33. Host Multiple HTML Pages

Suppose your project is:

```text
html-demo
│
├── index.html
├── about.html
├── contact.html
│
├── css
│   └── style.css
│
└── images
    └── logo.png
```

Deploy the structure into the application root.

For example:

```text
/home/site/wwwroot
│
├── index.html
├── about.html
├── contact.html
│
├── css
│   └── style.css
│
└── images
    └── logo.png
```

Then the URLs can be:

```text
https://your-app.azurewebsites.net/
```

```text
https://your-app.azurewebsites.net/about.html
```

```text
https://your-app.azurewebsites.net/contact.html
```

---

# 34. Add CSS

Project structure:

```text
html-demo
│
├── index.html
└── style.css
```

## `index.html`

```html
<!DOCTYPE html>
<html>
<head>
    <title>Azure Demo</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <h1>Azure App Service</h1>

    <p>My website is hosted on Azure.</p>

</body>
</html>
```

## `style.css`

```css
body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin-top: 100px;
}

h1 {
    font-size: 40px;
}

p {
    font-size: 20px;
}
```

Deploy:

```text
/home/site/wwwroot
│
├── index.html
└── style.css
```

---

# 35. Add JavaScript

Project structure:

```text
html-demo
│
├── index.html
├── style.css
└── script.js
```

## `index.html`

```html
<!DOCTYPE html>
<html>
<head>
    <title>Azure App Service</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <h1>Azure App Service</h1>

    <button onclick="showMessage()">Click Me</button>

    <script src="script.js"></script>

</body>
</html>
```

## `script.js`

```javascript
function showMessage() {
    alert("Hello from Azure App Service!");
}
```

Deploy:

```text
/home/site/wwwroot
│
├── index.html
├── style.css
└── script.js
```

---

# 36. Update the HTML Page

Suppose the original heading is:

```html
<h1>Welcome to Azure App Service</h1>
```

Change it to:

```html
<h1>Welcome to My Azure Website</h1>
```

Save the file.

Deploy the updated file again.

Refresh the website.

If the browser still displays the old version, use:

```text
Ctrl + F5
```

to perform a hard refresh.

---

# 37. Restart the App Service

If the application behaves unexpectedly, you can restart it.

Go to:

```text
App Service
    ↓
Overview
    ↓
Restart
```

Click:

```text
Restart
```

Wait for the App Service to become available again.

---

# 38. Stop and Start the App Service

From the App Service Overview page, you may see:

```text
Stop
```

and:

```text
Start
```

When an App Service is stopped, the website is unavailable.

Use this carefully, especially for production applications.

---

# 39. Important App Service Menu Items

## Overview

Provides information such as:

```text
App name
Status
Default domain
Resource group
Region
App Service Plan
```

## Deployment Center

Used to configure automated deployments from supported source-control/deployment systems.

## Configuration

Used for:

```text
Application settings
Environment variables
Connection strings
General settings
```

## Logs

Used for application and platform troubleshooting.

## Metrics

Can be used to monitor items such as:

```text
CPU
Memory
Requests
HTTP errors
```

## Networking

Contains networking-related configuration.

## TLS/SSL

Used for HTTPS and certificate-related configuration.

---

# 40. Troubleshooting

## Problem 1: Azure Default Page Appears

Check whether your file exists:

```text
/home/site/wwwroot/index.html
```

Make sure it contains your HTML code.

---

## Problem 2: 404 Not Found

Check:

```text
index.html
```

exists in:

```text
/home/site/wwwroot
```

Also verify the filename.

Correct:

```text
index.html
```

Potentially incorrect:

```text
Index.html
index.htm
index.HTML
```

Filename handling can depend on the platform and configuration.

---

## Problem 3: CSS Does Not Work

If the structure is:

```text
wwwroot
│
├── index.html
└── style.css
```

then use:

```html
<link rel="stylesheet" href="style.css">
```

If the structure is:

```text
wwwroot
│
├── index.html
└── css
    └── style.css
```

then use:

```html
<link rel="stylesheet" href="css/style.css">
```

The relative path must match the actual file structure.

---

## Problem 4: Images Do Not Appear

If the structure is:

```text
wwwroot
│
├── index.html
└── images
    └── logo.png
```

use:

```html
<img src="images/logo.png" alt="Logo">
```

Do not use:

```html
<img src="logo.png" alt="Logo">
```

unless `logo.png` is directly inside `wwwroot`.

---

## Problem 5: App Service Is Stopped

Go to:

```text
App Service
    ↓
Overview
```

Check the status.

It should indicate that the App Service is running.

If it is stopped, use:

```text
Start
```

---

## Problem 6: ZIP Has the Wrong Structure

Incorrect:

```text
website.zip
│
└── website
    └── index.html
```

Preferred deployment package structure:

```text
website.zip
│
└── index.html
```

The deployment package should contain the application files at the appropriate deployment root.

---

# 41. Security Considerations

Never put passwords or secret credentials inside HTML.

Do not put:

```text
Database passwords
API secret keys
Azure secrets
JWT secret keys
Private credentials
```

inside:

```text
index.html
```

Anything delivered to the browser can be inspected by the user.

For server-side applications, sensitive configuration should be stored using appropriate Azure App Service configuration/environment settings.

---

# 42. Azure App Service vs Azure Virtual Machine

If you have previously worked with an Azure Linux VM, this distinction is important.

## Azure Virtual Machine

With a VM, you generally manage:

```text
VM
│
├── Operating System
├── SSH
├── Users
├── Firewall
├── Web Server
├── Files
└── Application
```

Common commands include:

```bash
ssh
scp
apt
systemctl
nginx
apache
```

You have much more control over the operating system.

---

## Azure App Service

With App Service, Azure manages much of the underlying infrastructure.

You primarily work with:

```text
Application
    ↓
Deployment
    ↓
Configuration
    ↓
App Service
```

You generally do not need to manually manage:

```text
Operating system installation
OS patching
Network interface
SSH server
Web server infrastructure
```

This is one of the main characteristics of **PaaS — Platform as a Service**.

---

# 43. Azure VM vs App Service

| Feature | Azure VM | Azure App Service |
|---|---|---|
| Service Model | IaaS | PaaS |
| OS Management | User manages | Azure manages platform |
| SSH | Common | Usually not required |
| SCP | Common | Usually not required |
| Web Server | User manages | Platform-managed environment |
| Scaling | More manual | Built-in options |
| Deployment | Manual/automated | Multiple deployment options |
| Maintenance | Higher | Lower |
| Server Control | High | More limited |
| Typical Use | Full server control | Web applications |

---

# 44. Recommended Final Project Structure

For a slightly more complete classroom practical:

```text
azure-html-demo
│
├── index.html
├── style.css
└── script.js
```

## `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Azure App Service Demo</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <h1>Welcome to Azure App Service</h1>

    <p>This website is hosted on Microsoft Azure.</p>

    <button onclick="showMessage()">Click Me</button>

    <script src="script.js"></script>

</body>
</html>
```

## `style.css`

```css
body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin-top: 100px;
}

h1 {
    font-size: 40px;
}

p {
    font-size: 20px;
}
```

## `script.js`

```javascript
function showMessage() {
    alert("Hello from Azure App Service!");
}
```

Final Azure structure:

```text
/home/site/wwwroot
│
├── index.html
├── style.css
└── script.js
```

---

# 45. Complete Practical Flow

Remember the following sequence:

```text
1. Create index.html
        ↓
2. Test HTML locally
        ↓
3. Open Azure Portal
        ↓
4. Create Resource Group
        ↓
5. Create App Service
        ↓
6. Select Subscription
        ↓
7. Select Resource Group
        ↓
8. Enter unique Web App name
        ↓
9. Select Code
        ↓
10. Select supported runtime
        ↓
11. Select Linux
        ↓
12. Select Region
        ↓
13. Create/select App Service Plan
        ↓
14. Select Pricing Tier
        ↓
15. Review + Create
        ↓
16. Open App Service
        ↓
17. Get Default Domain
        ↓
18. Deploy HTML files
        ↓
19. Verify wwwroot
        ↓
20. Open Azure URL
        ↓
21. Website is live
```

---

# 46. Key Terms

## Resource Group

A logical container for Azure resources.

Example:

```text
rg-html-demo
```

## App Service

The Azure service hosting your web application.

Example:

```text
ashutosh-html-demo-2026
```

## App Service Plan

Provides the compute resources for the App Service.

Example:

```text
ASP-html-demo
```

## Default Domain

The public URL automatically provided by Azure.

Example:

```text
https://your-app-name.azurewebsites.net
```

## `wwwroot`

The application content directory.

Example:

```text
/home/site/wwwroot
```

## Kudu

An App Service management and troubleshooting environment that can provide deployment/debugging tools.

---

# 47. Final Result

After successful deployment:

```text
Browser
   │
   │ HTTPS
   ▼
https://your-app-name.azurewebsites.net
   │
   ▼
Azure App Service
   │
   ▼
/home/site/wwwroot
   │
   ├── index.html
   ├── style.css
   └── script.js
```

The HTML page is now publicly accessible through Azure App Service.

---

# 48. Practical Checklist

Use this checklist while performing the practical:

- [ ] Azure account is ready
- [ ] Azure Portal opened
- [ ] Resource Group created
- [ ] App Service created
- [ ] Unique Web App name selected
- [ ] Code deployment selected
- [ ] Supported runtime selected
- [ ] Linux selected
- [ ] Region selected
- [ ] App Service Plan created/selected
- [ ] Pricing tier selected
- [ ] App Service deployment completed
- [ ] Default domain obtained
- [ ] `index.html` created
- [ ] HTML tested locally
- [ ] HTML deployed
- [ ] `index.html` verified in application root
- [ ] Azure URL opened
- [ ] Website verified

---

# 49. One-Line Summary

```text
Create HTML → Create Resource Group → Create App Service → Configure Plan → Deploy HTML → Verify wwwroot → Open azurewebsites.net URL
```
