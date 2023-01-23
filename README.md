# Routing State with Nested Views
### Setting up Child (nested) State
```
.state('view1.child', {
    url: '/detail/{param1}',
    templateUrl: 'view1Detail.html',
    ...
});
```
__view1.html__ (parent state template)
```
<div>
    <div> content... </div>
    <ui-view></ui-view>
</div>
```
### Inherited resolve Properties
```
.state('view1', {
    resolve: {
        myData: 'someVal'
    }
    ...
});
```
```
.state('view1.child', {
    controller: "ChildCtrl as child"
    ...
});
```
```
ChildCtrl.$inject = ['myData'];
function ChildCtrl(myData){
    ...
};
```
***
#### _Summary_
* Nested states allow us to logically represent nested views.
* Parent state template has a ui-view in its template for the child state's template to insert its HTML.
* Child state name is usually declared with syntax `parent.child`.
* The optionally declared url of the child gets concatenated to the declared url of the parent.
* The parent's resolve property is inherited by the child and is injectable directly into the child's controller.
***