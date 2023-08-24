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





























