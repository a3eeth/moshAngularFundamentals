    ng g c courses -> courses.component.ts
generates components 

    ng g s courses -> courses.services.ts
generates services

# courses.component.ts
import crucial services from coupled service class 

    import { Component } from '@angular/core';
    import { CoursesService } from './courses.service';

# configure component declarator

    @Component({
     selector: 'app-this-component',
     template: '<h2>This template</h2>'
     )}
     
 > backtick to have directives within the template
     
     @Component({
      selector: 'app-this-component',
      template: `<ul><li *ngFor='let course of courses'>
                  {{ course }}
                 </li></ul>'
     
# configure export class + constructor with dependency injection
    export class CourseComponent {
    courses; //for storing the array
    //this is a dependency injection
    constructor(service: CoursesService){
     this.courses = service.getCourses();
    }
    
# courses.service.ts 
    export class CoursesService {
     getCourses(){
      return ['course_one', 'course_two', 'course_three'];
     }
    }
    
# app.module.ts
    @NgModule({
     declarations: [
      ...,
      CoursesComponent,
      ...
      ],
     providers: [
      ...,
      CoursesService,
      ...
     ]

