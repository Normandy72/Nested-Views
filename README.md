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