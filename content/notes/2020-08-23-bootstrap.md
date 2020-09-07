---
title: Bootstrap
author: Desmond Tuiyot
date: '2020-08-23'
slug: bootstrap
categories: []
tags:
  - bootstrap
---

## Forms

* Start with a `form` tag. In it, you wanna have `div` tags representing each form control and its label. 
  ```{html eval=F}
  <div class="form-group">
    <label for="inputEmail">Email</label>
    <input type="email" class="form-control" id="inputEmail" placeholder="Email">
  </div>
  ```
  * `form-control` is required for general styling and also sets the form controls to 100% width. For *file inputs* swap out `form-control` for `form-control-file`
    * To change width or use them inline, use predefined grid classes 
  * For a button - this doesn't need to be nested inside a `div`
    ```{html eval=F}
    <button type="submit" class="btn btn-primary">Submit</buttom>
    ```
* For horizontal forms - i.e. each form label and control are on one line, side by side
  ```{html eval=F}
  <div class="form-group row">
    <label for="inputEmail" class="col-sm-2 col-form-label">Email</label>
    <div class="col-sm-10">
      <input type="email" class="form-control" id="inputEmail" >
    </div>
  </div>
  ```
  * The `col-form-label` vettically centers the label to its corresponding form control
  