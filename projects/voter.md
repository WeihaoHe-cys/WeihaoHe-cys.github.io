---
layout: project
type: project
image: img/vote.jpg
title: "Voter Registration Application"
date: 2022-08-30
published: true
labels:
  - JavaScript
  - HTML
summary: "I developed this website with JavaScript and HTML to record Hawaii voter's information"
---

 1) The State ID number,first and last name, date of birth, mailing address, state, city, zip is not blank.
 2) Make sure the State ID number, zipcode, and phone number is correctly entered.
 3) Enusure the voter is US citizen, age of 16 and over, and Hawaii resident. And also ensure all radio buttons and affirm checkbox are checked.

Here is some code that illustrates how the program read values:

```cpp
document.voterapp.addEventListener("submit", function(eventParam){
 // What user enter for the State ID number
 let inputStateId = document.voterapp.idNum.value;
 //createing regex pattern for the state ID
 //Begins with uppercase S follow by 8 uppercase letter or digits
 let stateIdPattern = /^[A-Z][A-Z|0-9]{8}$/;

 //If the input is empty, sent an alert to the using to ask them input the ID Number
 if(inputStateId.length == 0 || inputStateId.length < 8){
   alert("ID Number Error: Please enter StateID number and length of the ID number is 8");
   eventParam.preventDefault();
   return;
 }
 else if(!stateIdPattern.test(inputStateId)){
   alert("ID Number Error: Must start with an S followed by 8 uppercase letters or digits.");
   eventParam.preventDefault();
   return;
 }

 //validate birthdate is entered
 //retrieve the value from the dob tag and store in a variable
 let birthdateValue = document.voterapp.dob.value;

 if(birthdateValue.length == 0){
   alert("Error: Please enter your date of birth.");
   eventParam.preventDefault();
   return;
 }

//validating the length of lastname and make sure is not blank
//retrieve lastname value and store it in a variable
 let lastNameValue = document.voterapp.lastname.value;
 if(lastNameValue.length == 0){
   alert("Error: Last name cannot be blank.");
   eventParam.preventDefault();
   return;
 }
//validating the length of firstname and make sure is not blank
//retrieve firstname value and store it in a variable
let firstNameValue = document.voterapp.firstname.value;
if(firstNameValue.length == 0){
  alert("Error:  First name cannot be blank.");
  eventParam.preventDefault();
  return;
}

//validating the length of mailing address and make sure is not blank
//retrieve mailling address value and store it in a variable
let maillingAddress1 = document.voterapp.address1.value;
if(maillingAddress1.length == 0){
  alert("Error:  Address Line 1 cannot be blank.");
  eventParam.preventDefault();
  return;
}

//validating the length of mailing city and states and make sure is not blank
//retrieve mailling city and state value and store it in a variable
let mailingCityValue = document.voterapp.city.value;
let mailingStateValue = document.voterapp.state.value;

if(mailingCityValue.length == 0){
  alert("Error: City cannot be blank.");
  eventParam.preventDefault();
  return;
}
if(mailingStateValue.length == 0){
  alert("Error: State cannot be blank.");
  eventParam.preventDefault();
  return;
}

//Validating Mailing ZIP code must be a Hawaii ZIP code that also accepts the optional 4 digit extension:
//5 digits that start with 967 or 968 OR 5 digits that start with 967 or 968 followed by a -, followed by 4 digits.

//Validating Mailing ZIP code must be a Hawaii ZIP code that also accepts the optional 4 digit extension:
//5 digits that start with 967 or 968 OR 5 digits that start with 967 or 968 followed by a -, followed by 4 digits.
let zipcodeValue = document.voterapp.zip.value;
let zipcodeRegex = /^96[78]\d\d(-\d{4})?$/;

if(zipcodeValue.length == 0){
 alert("Error: Please Enter your zipcode.");
 eventParam.preventDefault();
 return;
}
else if(!zipcodeRegex.test(zipcodeValue)){
 alert("Error: ZIP code is not a Hawaii ZIP code.");
 eventParam.preventDefault();
 return;
}

// Ensure the contact phone number only accepts input in the pattern:
//000-000-0000 or 0000000000
//3 digits, followed by a -, followed by 3 digits, followed by a -, followed by 4 digits.
//Or 10 digits
//Example: 123-456-7890 or 1234567890
let phoneNumValue = document.voterapp.phone.value;
let phoneRegexDash = /^\d{3}-\d{3}-\d{4}$/;
let phoneRegex = /^\d{10}$/;


if(!phoneRegexDash.test(phoneNumValue) && !phoneRegex.test(phoneNumValue)){
 alert("Error: Please enter a phone number in the form 000-000-0000 or 0000000000.");
 eventParam.preventDefault();
 return;
}

// making sure user answer the citizen question
// validating whether if the user is a citizen in US.
let citizenRadio = document.voterapp.amCitizen.value;
let citizenElements = document.getElementById("amCitizenNo");

if(citizenElements.checked){
  alert("Error: Non US citizens are not eligible to vote");
  eventParam.preventDefault();
  return;
}
```