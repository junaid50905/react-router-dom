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


#### Link: when we will click the Link element it works like a button and it will navigate use to a path
```
<Link to="/about">About</Link>
```
