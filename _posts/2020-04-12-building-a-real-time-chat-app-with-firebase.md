---
title: Building a Real-Time Chat App with Firebase
image: "/assets/firebase.png"
---

<img class="width-100" src="/assets/firebase.png"/>

Out of the box, Firebase provides lots of server side side so that we can just concentrate on building the front end and UX of our chat app.

Below are few things that Firebase gives us.

1. Authentication: This includes support for email and password authentication as well as single sign-on capabilities (via Facebook, Twitter and Google).
1. Realtime database: This is a “NoSQL” database that updates in real time.
1. Cloud functions: These run extra server-side logic.
1. Static hosting: This is a means of serving assets pre-built instead of rendering at runtime.
1. Cloud storage: This gives us a place to store media assets.


# If you want to start playing with the app right away, here's the link to a working Firebase chat app with complete free source code.

https://github.com/iamnaveenpaul/firebase-chat-app


# Signup for Firebase to authenticate users
Firechat requires Firebase in order to authenticate users and store data. You can sign up  for a free account.
https://console.firebase.google.com/u/0/?utm_source=firechat&pli=1


# How to setup Firebase with a Jquery app
Firechat uses the Firebase Realtime Database as a backend, so it requires no server-side code. It can be added to any web app by including a few JavaScript files:

```

<!-- jQuery -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

<!-- Firebase -->
<script src="https://www.gstatic.com/firebasejs/3.3.0/firebase.js"></script>

<!-- Firechat -->
<link rel="stylesheet" href="https://cdn.firebase.com/libs/firechat/3.0.1/firechat.min.css" />
<script src="https://cdn.firebase.com/libs/firechat/3.0.1/firechat.min.js"></script>
```

# Allow your users to authenticate in Firebase app:
```

<script>
  function login() {
    // Log the user in via Twitter
    var provider = new firebase.auth.TwitterAuthProvider();
    firebase.auth().signInWithPopup(provider).catch(function(error) {
      console.log("Error authenticating user:", error);
    });
  }

  firebase.auth().onAuthStateChanged(function(user) {
    // Once authenticated, instantiate Firechat with the logged in user
    if (user) {
      initChat(user);
    }
  });
</script>

<button onclick="login()">Login with Twitter</button>
```

# How to initialize Firebase chat

```
<script>
  function initChat(user) {
    // Get a Firebase Database ref
    var chatRef = firebase.database().ref("chat");

    // Create a Firechat instance
    var chat = new FirechatUI(chatRef, document.getElementById("firechat-wrapper"));

    // Set the Firechat user
    chat.setUser(user.uid, user.displayName);
  }
</script>

<div id="firechat-wrapper"></div>
```