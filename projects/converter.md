---
layout: project
type: project
image: img/spam_musubi.jpg
title: "Recipe converter"
date: 2022-08-30
published: true
labels:
  - JavaScript
  - HTML
summary: "I developed this website with JavaScript and HTML to convert amount of materials needed to make the spam musubi based on the quantity needed."
---

With the quantity changes, materials quantity will adjust accordingly. 

Here is some code that illustrates how the program read values:

```cpp
let servingElemments = document.getElementById("inputServings");
let resetButtonElements = document.getElementById("resetRecipe");
let canSpamElements = document.getElementById("inputCanSpam");
let noriElements = document.getElementById("inputNori");
let riceElements = document.getElementById("inputRice");
let originalServings = 8;
let originalCanSpam = 1;
let originalNori = 4;
let originalRice = 6;

resetButtonElements.addEventListener("click", function() {
  servingElemments.value = originalServings;
  canSpamElements.value = originalCanSpam;
  noriElements.value = originalNori;
  riceElements.value = originalRice;
})

servingElemments.addEventListener("change", function() {
  let newRatio = servingElemments.value / originalServings;
  canSpamElements.value = newRatio * originalCanSpam;
  noriElements.value = newRatio * originalNori;
  riceElements.value = newRatio * originalRice;
})

canSpamElements.addEventListener("change", function() {
  if(canSpamElements.value < 0){
    let changeNegToPos = canSpamElements.value * -1;
    window.alert("Negative number is not valid for calculation. Change " + canSpamElements.value + " to " + changeNegToPos);
    let negNewRatio = changeNegToPos / originalCanSpam;
    canSpamElements.value = changeNegToPos;
    servingElemments.value = negNewRatio * originalServings;
    noriElements.value = negNewRatio * originalNori;
    riceElements.value = negNewRatio * originalRice;
  }
  else{
    let newRatio = canSpamElements.value / originalCanSpam;
    servingElemments.value = newRatio * originalServings;
    noriElements.value = newRatio * originalNori;
    riceElements.value = newRatio * originalRice;
  }

})

noriElements.addEventListener("change", function() {
  if(noriElements.value < 0){
    let changeNegToPos = noriElements.value * -1;
    window.alert("Negative number is not valid for calculation. Change " + noriElements.value + " to " + changeNegToPos);
    let negNewRatio = changeNegToPos / originalNori;
    noriElements.value = changeNegToPos;
    servingElemments.value = negNewRatio * originalServings;
    canSpamElements.value = negNewRatio * originalCanSpam;
    riceElements.value = negNewRatio * originalRice;
  }
  else{
    let newRatio = noriElements.value / originalNori;
    canSpamElements.value = newRatio * originalCanSpam;
    servingElemments.value = newRatio * originalServings;
    riceElements.value = newRatio * originalRice;
  }
})

riceElements.addEventListener("change", function() {
  if(riceElements.value < 0){
    let changeNegToPos = riceElements.value * -1;
    window.alert("Negative number is not valid for calculation. Change " + riceElements.value + " to " + changeNegToPos);
    let negNewRatio = changeNegToPos / originalRice;
    riceElements.value = changeNegToPos;
    servingElemments.value = negNewRatio * originalServings;
    canSpamElements.value = negNewRatio * originalCanSpam;
    noriElements.value = negNewRatio * originalNori;
  }
  else{
    let newRatio = riceElements.value / originalRice;
    servingElemments.value = newRatio * originalServings;
    noriElements.value = newRatio * originalNori;
    canSpamElements.value = newRatio * originalCanSpam;
  }
})
```