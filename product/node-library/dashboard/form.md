---
description: Adds a form to the Maya dashboard.
---

# Form

Helps to collect multiple value from the user on submit button click as an object in `msg.payload`

Multiple input elements can be added using add elements button

Each element contains following components:

* **Label** : Value that will be the label of the element in the user interface
* **Name** : Represents the key (variable name) in the `msg.payload` in which the value of the corresponding element present
* **Type** : Drop drown option to select the type of input element
* **Required** : On switching on the user has to supply the value before submitting
* **Rows** : number of UI rows for multiline text input
* **Delete** : To remove the current element form the form

Optionally the **Topic** field can be used to set the `msg.topic` property.

The Cancel button can be hidden by setting it's value to be blank "".
