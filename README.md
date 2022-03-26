# Group Project - *TinderClone*

**TinderClone** is a dating app.

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
1. [Schema](#Schema)

## Overview
### Description
A dating app that allows user to match with potential partners based on matching with other user profiles. This app will utilize a database and the swipe cards feature.

### App Evaluation
- **Category:** Social Networking / Dating
- **Mobile:** This app would be primarily developed for mobile but would perhaps be just as viable on a computer, such as tinder or other similar apps. Functionality wouldn't be limited to mobile devices, however mobile version could potentially have more features.
- **Story:** Analyzes users potential matches, and connects them to other users that liked each other. The user can then decide to message this person.
- **Market:** Any individual could choose to use this app, and to keep it a safe environment.
- **Habit:** This app could be used as often or unoften as the user wanted depending on how deep their social life is, and what exactly they're looking for.
- **Scope:** We would start with pairing people based on a person liking another person's profile. Then perhaps this could evolve into a dating application that allows users to find other types of matches. For example, friends and/or business partners.

## Product Spec
### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* User can sign up to create a new account.
* User can log in and log out of his or her account.
* Profile pages for each user.
* User can swipe right or left to match or pass according to their selected gender preference.
* Matches have a chat window to get to know each other.

**Optional Nice-to-have Stories**

* Users can use their current location to match with nearby users.
* Add a page for preferences (set distance based on user location).
* Users can link their instagram and/or Spotify onto their profile.
* Add an option for people looking to match with friends only.
* Add an option for people looking to match with business partners only.

### 2. Screen Archetypes

* Login 
* Register - User signs up or logs into their account
   * Upon Download/Reopening of the application, the user is prompted to log in to gain access to their profile information to be properly matched with another person. 
* Messaging Screen - Chat for users to communicate (direct 1-on-1)
   * Upon swiping right, users are matched and message screen opens
* Profile Screen 
   * Allows user to upload a photo and fill in information that is interesting to them and others
* Swipe Cards Stack.
   * Allows user to view the card stack and swipe right/left in order to match or pass.
* Settings Screen
   * Lets people change gender preference.

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Matching -> Showing the cards of profiles and being able to swipe right/left in order to match or pass.
* Messages and Matches -> Top portion showing new matches while bottom showing current messages.
* Profile -> Your profile page with buttons to lead to settings for matches and personal information editing. 
 

**Flow Navigation** (Screen to Screen)
* Forced Log-in -> Account creation if no log in is available or jumps to log in screen if chosen.
* Register -> After entering your first time registertaion info you're sent to the matching page. 
* Profile -> Options to either change your profile information or see your settings and have option to logout  

## Wireframes
<img src="https://i.imgur.com/xw66Eew.jpg" width=800><br>

### [BONUS] Digital Wireframes & Mockups
<img src="" height=200>

### [BONUS] Interactive Prototype
<img src="" width=200>

## Schema 
### Models
#### Post

   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | objectId      | String   | unique id for the user post (default field) |
   | author        | Pointer to User| image author |
   | image         | File     | image that user posts |
   | caption       | String   | image caption by author |
   | commentsCount | Number   | number of comments that has been posted to an image |
   | likesCount    | Number   | number of likes for the post |
   | createdAt     | DateTime | date when post is created (default field) |
   | updatedAt     | DateTime | date when post is last updated (default field) |
### Networking
#### List of network requests by screen
   - Home Feed Screen
      - (Read/GET) Query all posts where user is author
         ```swift
         let query = PFQuery(className:"Post")
         query.whereKey("author", equalTo: currentUser)
         query.order(byDescending: "createdAt")
         query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
            if let error = error { 
               print(error.localizedDescription)
            } else if let posts = posts {
               print("Successfully retrieved \(posts.count) posts.")
           // TODO: Do something with posts...
            }
         }
         ```
      - (Create/POST) Create a new like on a post
      - (Delete) Delete existing like
      - (Create/POST) Create a new comment on a post
      - (Delete) Delete existing comment
   - Create Post Screen
      - (Create/POST) Create a new post object
   - Profile Screen
      - (Read/GET) Query logged in user object
      - (Update/PUT) Update user profile image
#### [OPTIONAL:] Existing API Endpoints
##### An API Of Ice And Fire
- Base URL - [http://www.anapioficeandfire.com/api](http://www.anapioficeandfire.com/api)

   HTTP Verb | Endpoint | Description
   ----------|----------|------------
    `GET`    | /characters | get all characters
    `GET`    | /characters/?name=name | return specific character by name
    `GET`    | /houses   | get all houses
    `GET`    | /houses/?name=name | return specific house by name

##### Game of Thrones API
- Base URL - [https://api.got.show/api](https://api.got.show/api)

   HTTP Verb | Endpoint | Description
   ----------|----------|------------
    `GET`    | /cities | gets all cities
    `GET`    | /cities/byId/:id | gets specific city by :id
    `GET`    | /continents | gets all continents
    `GET`    | /continents/byId/:id | gets specific continent by :id
    `GET`    | /regions | gets all regions
    `GET`    | /regions/byId/:id | gets specific region by :id
    `GET`    | /characters/paths/:name | gets a character's path with a given name

## License

    Copyright [2022] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
