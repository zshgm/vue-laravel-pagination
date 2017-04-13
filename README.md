# vue-laravel-pagination
A simple vue.js component to paginate data in Laravel

Example of use:
```
<pagination :pagination="pagination" :callback="search" :offset="3"></pagination>
```
Will be generated:
```
<div class="pagination">
  <a href="#">«</a>
  <a href="#">1</a>
  <a href="#" class="active">2</a>
  <a href="#">3</a>
  <a href="#">»</a>
</div>
```
