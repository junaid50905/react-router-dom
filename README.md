# react-router-dom

#### BrowserRoute: which will wrap the whole application
```
<BrowserRoute>
  <App/>
</BrowserRoute>
```
#### Routes: which will wrap all of the Route
```
<Routes>
  <Route path="/" element={<Home/>}/>
  <Route path="/about" element={<About/>}/>
  <Route path="/shop" element={<Shop/>}/>
</Routes>
```


#### Link: When we click the Link element it works like a button and it will navigate us to a path
```
<Link to="/about">About</Link>
```

#### NavLink: We will use this as a nav item of navigation
We can use it Bootstrap nav
```
<nav>
  <NavLink to="/" className="nav-link active">Home</NavLink>
  <NavLink to="/about" className="nav-link">About</NavLink>
  <NavLink to="/shop" className="nav-link">Shop</NavLink>
</nav>

There are several ways to activate a NavLink.

1.
<a href="https://ibb.co/WgL6spT"><img src="https://i.ibb.co/WgL6spT/active-navlink.png" alt="active-navlink" border="0"></a>

2.
<a href="https://ibb.co/1qKXt91"><img src="https://i.ibb.co/1qKXt91/active-navlink-2.png" alt="active-navlink-2" border="0"></a>

3. we can do it for bootstrap simply


#### Route parameter, pass parameter, getting data according to the parameter
Shop.jsx
```
<Link to={`/shop/${id}`}>Go to product detailed</Link>
```

Routes
```
<Route path="/shop/:id" element={<ProductDetailed/>}/>
```

ProductDetailed.jsx

<a href="https://ibb.co/q1NFV6F"><img src="https://i.ibb.co/q1NFV6F/Product-detailed.png" alt="Product-detailed" border="0"></a>


## Nested Routes

<a href="https://ibb.co/BqJ5zL2"><img src="https://i.ibb.co/BqJ5zL2/nested-routing.png" alt="nested-routing" border="0"></a>

here, we making a nested routes for host


Navbar.jsx
```
import {Link} from "react-router-dom"

const Navbar = () => {
  return (
    <nav>
      <Link to="/">Home</Link><br />
      <Link to="/host">Host</Link><br />
      <Link to="/team">Team</Link><br />
      <Link to="/profile">Profile</Link><br />
      <hr />
    </nav>
  )
}

export default Navbar

```


App.jsx
```
<>
  <Navbar/>
  <Routes>
    <Route path="/host" element={<HostLayout/>}>
      <Route path="/host" element={<Dashboard/>}/>
      <Route path="/host/income" element={<Income/>}/>
      <Route path="/host/reviews" element={<Reviews/>}/>
    </Route>
  </Routes>
</>
```
##### NOTE: nested route er somoy parent("/host" of HostLayout) er nicher content Outlet a show hobe. Outlet ache jekhane nested route er content show hobe sekhane.

HostLayout.jsx
```
import { Link,Outlet } from 'react-router-dom';

const HostLayout = () => {
  return (
    <div>
          <Link to="/host">Dashboard</Link><br />
          <Link to="/host/income">income</Link><br />
          <Link to="/host/reviews">reviews</Link><br />
          <hr />
          <Outlet />
    </div>
  )
}

export default HostLayout

```

when we click host from the Navbar then go to the /host route and this host route will call Dashboard component as default


#### Relative path


App.jsx (before relative path)
```
<>
  <Navbar/>
  <Routes>
    <Route path="/host" element={<HostLayout/>}>
      <Route path="/host" element={<Dashboard/>}/>
      <Route path="/host/income" element={<Income/>}/>
      <Route path="/host/reviews" element={<Reviews/>}/>
    </Route>
  </Routes>
</>
```

App.jsx (after relative path)
```
<>
  <Navbar/>
  <Routes>
    <Route path="host" element={<HostLayout/>}>
      <Route path="host" element={<Dashboard/>}/>
      <Route path="income" element={<Income/>}/>
      <Route path="reviews" element={<Reviews/>}/>
    </Route>
  </Routes>
</>
```
here, host is the parent path so we don't need to write the host again. income and reviews route will work but Dashboard will not work. through the index route we will learn it

#### index route

```
<>
  <Navbar/>
  <Routes>
    <Route path="host" element={<HostLayout/>}>
      <Route index element={<Dashboard/>}/>
      <Route path="income" element={<Income/>}/>
      <Route path="reviews" element={<Reviews/>}/>
    </Route>
  </Routes>
</>
```

#### Suppose we have products and product detailed routes then how we will make it a nested route

before nested route
```
<>
    <Route path="products" element={<Products/>}/>
    <Route path="product/:id" element={<ProductDetailed/>}/>
</>
```

after nested route
```
<>
<Route path="products">
    <Route index element={<Products/>}/>
    <Route path=":id" element={<ProductDetailed/>}/>
</Route>
</>
```
##### NOTE: but do not need to write only for two routes

##### questions on the nested route:

- Why we will use nested route?
  
    when we have a shared route then we can use nested route
    ```
      <Route path="host" element={<Dashboard/>>} />
      <Route path="host/income" element={<Income/>>} />
      <Route path="host/reviews" element={<Reviews/>>} />

      <Route path="host" element={<HostLayout/>}>
        <Route index element={<Dashboard/>}/>
        <Route path="income" element={<Income/>}/>
        <Route path="reviews" element={<Reviews/>}/>
      </Route>
      
    ```
  
- What is the Layout route?
  
  It is the parent route of some nested routes Link
  
HostLayout.jsx
```
import { Link,Outlet } from 'react-router-dom';

const HostLayout = () => {
  return (
    <div>
          <Link to="/host">Dashboard</Link><br />
          <Link to="/host/income">income</Link><br />
          <Link to="/host/reviews">reviews</Link><br />
          <hr />
          <Outlet />
    </div>
  )
}

export default HostLayout

```

- What is the index route?

  It is the default route

### Create a proper layout of the application

```
<Header/>
<main>
  <Outlet/>
</main>
<Footer/>

```
















