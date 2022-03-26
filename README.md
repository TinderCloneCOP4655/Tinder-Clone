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
#### Matches

   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | UserId      | String | unique id for the user profile (default field) |
   | name        | String | user's name |
   | ProfileImageUrl | String | image that user uploads |
   | chatId       | String | chat id for matching users |
   
### Networking
#### List of network requests by screen
   - Login/Registration Screen
      - (Create/POST) create new user
      - (Read/GET) log in existing user
   - Card Stack Screen
      - (Read/GET) Cycle the card stack with opposite sex users
      - (Create/POST) Register a swipe(right;like)
         * Registering a swipe(left;dislike) is not needed.
   - Chat Screen
      - (Read/GET) Read matches
      - (Create/POST) Create a new chat
      - (Read/GET) Read message 'from'
      - (Create/POST) Send message 'to'
   - Profile Screen
      - (Read/GET) Query logged in user object
      - (Update/PUT) Update user profile information

#### [OPTIONAL:] Existing API Endpoints
- ...

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
