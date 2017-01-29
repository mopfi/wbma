class: center, middle

# WBMA, Angular HTTP Client

## 3/2017

---
# Routing

1. Create new app with Angular CLI
2. Create components 'front', 'top-bar', 'register' and 'login'
3. Template for 'top-bar' component:
```
  <nav>
      <ul>
        <li>
            <a [routerLink] = "'/front'">Front page</a>
        </li>
        <li>
            <a [routerLink] = "'/login'">Login</a>
        </li>
        <li>
            <a [routerLink] = "'/register'">Register</a>
        </li>
      </ul>
  </nav>
```
4. Template for 'front' component:
```
<div>Display this content when logged in.</div>
```
5. Create templates for 'login' and 'register' components yourself
6. For routing edit '/app/app.module.ts/':
- Before @NGModule add this:
```
const routeConfig = [
  {
    path: '',
    pathMatch: 'full',
    redirectTo: '/login'
  },
  {
    path: 'login',
    component: LoginComponent
  },
  {
    path: 'register',
    component: RegisterComponent
  },
  {
    path: 'logout',
    component: LogoutComponent
  },
  {
    path: 'front',
    component: FrontComponent
  }
];
```
- Edit the imports-array like this:
```
...
imports: [
    BrowserModule,
    FormsModule,
    HttpModule,
    RouterModule.forRoot(routeConfig)
  ],
  ...
```
7. Edit 'app.component.html' to this:
```
<app-top-bar></app-top-bar>
<router-outlet></router-outlet>
```
8. Now the navigation should work.

___

# Using services II - Login

1. Create new folder 'services' to 'app'-folder
2. Create new service 'media' to services folder ```ng g s services/media```
3. In the service create methods 'register' and 'login' with corresponding functionalities
- 'login': call media API to login user and save users data to [local storage](http://www.w3schools.com/html/html5_webstorage.asp)
    - when logged in, user is redirected to 'front'
    - if user has already logged in redirect to 'front' (autodirect)
- 'register': call media API to create new user and automatically login


---