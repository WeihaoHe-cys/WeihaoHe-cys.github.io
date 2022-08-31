---
layout: project
type: project
image: img/Vending_Machine.jpg
title: "Vending Machine"
date: 2022-08-30
published: true
labels:
  - JAVA
summary: "Used to implement into a vending machine to add the food objects, set the item price, remove items, output the list of items purchased and the price."
---

<div class="text-center p-4">
  <img width="200px" src="../img/micromouse/micromouse-robot.png" class="img-thumbnail" >
  <img width="200px" src="../img/micromouse/micromouse-robot-2.jpg" class="img-thumbnail" >
  <img width="200px" src="../img/micromouse/micromouse-circuit.png" class="img-thumbnail" >
</div>

Vending Machin algorithms would creatd a list and adding the nodes to the list.
It would display the the menus first, and receive inputs from users.
When adding the item, program receive the name, price, calories etc. Then it creates the food node and adding it to the list.
It will check if the node already exist in the list first before adding the item. 

Here is some code that illustrates how the program read values:

```cpp
   public boolean checkBarcode(int barcode){
      SNode cursor = front; //create cursor referencing the front
   
      for(int i=0; i < sizeCount; i++) {//for loop to check for each nodes in the list
         if(cursor.getSnack().getBarcode() == barcode) { //node - snack - barcode 
            return true; // if the barcode match, return true
         }
         else{
            cursor = cursor.getNext(); //make the cursor pointing at the next node if barcode not matching
         }
      }    
      return false; // loop through the list, if no matching barcode found, return false
   }
   
    /** method to add new nodes in the list
     * @para          Snack object
     **/
   public void add(Snack snack) {
      SNode n = new SNode(snack); // make a node
      
      // if list is empty 
      if (sizeCount == 0) {
         front = n;
         back = n;
         sizeCount++;
      } 
      
      // if list is populated, point previous node to new node, assign new node to last
      else {
         back.setNext(n); //front stay at its position back move to the next node added
         back = n;
         sizeCount++; // incrementing the size of the list       
      }
   }

```

