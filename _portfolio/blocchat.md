---
layout: post
title: Bloc Chat
feature-img: "img/header_image.png"
thumbnail-path: "img/blocchatMain.png"
short-description: Bloc Chat is a real-time chat application.

---
{:.center}
## Bloc Chat: Efficiently simplistic.

This online chat application provides users with an efficient and user-friendly way to communicate with family, friends and colleagues. Bloc Chat requires nothing more than an internet connection and a username for you to access any chatroom you wish to choose or create. Happy chatting!

![]({{ site.baseurl }}/img/blocchatMain.png)
---
## Why Bloc Chat?

Bloc Chat is a **S**ingle **P**age **A**pplication**(SPA)** built with Google's AngularJS framework, Twitter's Bootstrap library and Google's Firebase Realtime Database. The primary motivator behind Bloc Chat was knowledge. I am (at the time of writing this) relatively new to AngularJS and this served as my maiden voyage into the framework and its nuances. Additionally, I had **zero** experience with Twitter's Bootstrap or Google's Firebase before this project. So, while the goal of this project was in fact to build a simple chat-based SPA, in the grand scheme of my coding career this was merely a small step in my never-ending quest to stay on top of industry leading technologies.

![]({{ site.baseurl }}/img/bootstrap_angularjs.png)

---
## Adversity

I wanted to create a chat application that could be used by even the most technologically challenged of us all! Choose a username, select a chatroom and chat. It really is that simple, at least from the user's perspective...

The first hurdle I faced was related to Google's Firebase's **non-relational** database concept. Before Bloc Chat my database experience was strictly with standard, relational, table-like databases that you typically find when working with SQL or other similar applications. Non-relational databases, on the other hand, represent data in collections of **JSON** documents. While there was definitely an acclimation period, Firebase's UI and documentation made the concept easy to grasp while simultaneously highlighting the benefits offered by non-relational databases opposed.


![]({{ site.baseurl }}/img/relational_vs_nonrelational_databases.png)

Another challenge I faced while developing Bloc Chat was implementing the modal functionality. Initially, I was unsure of which available method to initiate a modal was considered _best-practice_ within the industry. I ultimately decided to utilize Bootstrap's **$uibModal** and **$uibModalInstance** services to achieve my desired result. $uibModal is a service to create modal windows. As I dug into Boostrap's documentation I quickly realized that creating modals with this services is simple, powerful and straightforward: _create a template and controller, and reference them when using $uibModal._ The $uibModal service has only one method: **open(options)**, but has dozens and dozens of parameters you can utilize in order to customize your modal's functionality.


{% highlight javascript %}
$uibModal.open({
    ariaLabelledBy: 'modal-title',
    ariaDescribedBy: 'modal-body',
    templateUrl: 'templates/newRoomModal.html',
    controller: 'ModalInstanceCtrl',
    controllerAs: 'modalControl',
});
{% endhighlight %}

The third key piece of adversity I faced was due to my inexperience with Bootstrap's grid system. While the concept of a grid system is undoubtedly straightforward, each system comes with its own set of nuances and rules. Bootstrap offers a responsive, mobile first fluid grid system that revolves around 12, appropriately scaled columns that adapt to your screen or container size. Bootstrap offers several predefined classes to allow users to quickly get their application up and running while also providing more powerful _mixins_, which allow for further layout customization.

![]({{ site.baseurl }}/img/bootstrap_grid-system.png)
---

## I think I can, I think I can...

By building Bloc Chat as an SPA I was able to create a straight-forward chat site that only utilizes one view and one modal. AngularJS is a powerful framework and I enjoyed the challenges I faced while developing this application. Angular, or more so an SPA in general, made a lot of sense for this project, since chat applications are real-time programs. If Bloc Chat had been built using HTML, CSS, and JavaScript, a new server request would have been sent every time a new message was sent or received, which would be inconvenient and inefficient. Angular eliminated the need for page refreshes, which worked perfectly for a project of this nature.

The perfect compliment to AngularJS for this project was Google's Firebase, which allowed me to easily store and manipulate chat and user data. Although, as previously mentioned, I had never utilized a non-relational database before, it actually ended up being straightforward. I was able to query my desired data using just a few short lines of javascript. I then used the data stored in my **$firebasearray** within an **ng-repeat** block in my HTML to display all of the messages for the active room. Firebase automatically sorts the array based on when the data was submitted to the database, so no further manipulation was needed for the messages to appear in sequential order. The key attribute that made Firebase perfect for my Bloc Chat application is the fact that the database updates in **real-time**. As soon as a message is sent to a chat room, that message appears immediately, with no need to refresh the webpage or any other user manipulation.

{% highlight javascript %}
var ref = firebase.database().ref().child("messages");
var messages = $firebaseArray(ref);
{% endhighlight %}


Lastly, I had to ensure that every user chose a username before sending messages. I achieved this through the use of cookies. Firebase offers a few built-in functions for managing and manipulating cookies. This made the process extremely easy once I found the proper documentation. This step not only significantly increased my knowledge of cookies and their functionality in general, but also led to my exploration of the developer tools offered through the Google Chrome Web Browser. Who knew you could see all the cookies stored for a particular website with just a few mouse clicks? I sure didn't!

![]({{ site.baseurl }}/img/cookies.png)


---
## Time to Chat!

Well, that wraps up my journey through my first AngularJS SPA! AngularJS, Bootstrap and Firebase worked in perfect harmony to allow me to build this simple and efficient chat application. I highly recommend building an application that uses these tools if you are not familiar with them. Not only are all of these resources powerful industry leaders, but they are also fun to use and vital to hone as you progress with your software development career. Despite some challenges I faced along the way, I had a lot of fun making this application and I hope to expand upon its capabilities in the near future!
