---
title : "MVC Pattern"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.1.2 </b> "
---

**MVC** (Model-View-Controller) is a software architecture model that helps manage and build software projects more systematically.

**MVC** stands for:
1. **Model**: Represents the data and logic of the application. Model often contains information about objects and perform data-related operations such as database retrieval.
2. **View**: Display data to the user. View receives data from Model and displays them in an appropriate way. This includes initializing the user interface and displaying data on it.
3. **Controller**: Is an intermediary component between Model and View. Controller receives requests from users through the interface (View), then processes the request, interact with the Model to retrieve or update data, and then return the results to View to display to the user.

![MVC](/Dung_aws/images/2.1/0002.png)




