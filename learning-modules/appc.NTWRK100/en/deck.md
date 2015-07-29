theme:appcelerator-training
tableclass:striped
progress:true

# Networking

Appcelerator SDK Fundamentals

---cover

# Networking

## Appcelerator SDK Fundamentals

--- 

# In this lesson, you will:

- Explore the purpose of modules and identify sources of modules
- Install a module for use in an Appcelerator project

---section 

# MODULE OVERVIEW & QUICK-TOUR

--- 

# Appcelerator Modules

![img](/assets/image6.png)

- Add 'missing' features
- Narrow use cases
- Appcelerator & Community created
- Free, one-time, & subscription-based
- Can connect to enterprise data sources

--- 

# Module Distribution

- Some distributed with Appcelerator
  - Need to be loaded via ```tiapp.xml```
- Download from [Appcelerator Marketplace](http://marketplace.appcelerator.com)
- Community developed:
  - [http://www.github.com](http://www.github.com)
  - [http://www.gitt.io](http://www.gitt.io)
- Variety of licensing options
  - Per month, per user, per app, free

--- 

# Built-in Modules

![img](/assets/image7.png)

--- 

# Appcelerator Open Source Modules

Available at [http://github.com/appcelerator/titanium_modules](http://github.com/appcelerator/titanium_modules)

![img](/assets/image8.png)

--- 

# Appcelerator Marketplace

![img](/assets/image9.png)

--- 

# PayPal (iOS and Android)

![img](/assets/image11.png)

- Mobile Payments Library
- Requires PayPal merchant account
- In development, uses sandbox environment, in production uses live servers

--- 

# StoreKit & In-App Billing

- StoreKit — iTunes App Store integration
- In-App Billing — Google Play integration
- StoreKit can be used for in-app purchases, digital goods
- Free from Appcelerator

--- 

# Advertising modules

- Admob, Millennial Media, Greystripe, and InMobi from Appcelerator
- Tap for Tap, Flurry/AppCircle, and more from third-parties
- Some free, some not

--- 

# Community Contributions

![img](/assets/image12.png)
![img](/assets/image13.png)

---section 

# INSTALLING MODULES

--- 

# Installing a Module

![img](/assets/image14.png)

- Download zip file, or copy URL to zip file
- Choose Help, Install Mobile Module
- Paste URL or browse to location
- Choose Titanium SDK (for use in all future projects) or a specific project

--- 

# Manually Installing for a Single Project

1. Download zip file
2. Place in project's root directory
3. Build once — to unzip and create necessary folders

--- 

# Manually Installing for Multiple Projects

- Download zip file
- Unzip to ```%TITANIUM_INSTALL_DIR%/modules``` directory

![img](/assets/image15.png)

---section 

# LOADING & USING MODULES

--- 

# Loading a Module

![img](/assets/image16.png)

--- 

# View-based Modules

![img](/assets/image17.png)

--- 

# Modules in the Controller

- Must ```require()``` module in your controller to use its functions
- (Every marketplace module comes with example and doc)

![img](/assets/image18.png)

--- 

# Summary

In this lesson, you:

- Explored the purpose of modules and identified sources of modules
- Installed a module for use in an Appcelerator project

---section

# Questions?