## summery

### Router Components
- BrowserRouter


### Components
- Routes & Route

path: path of the route <br>
element: <br>
index: it is used to indicate the parent path of the nested route<br>
```
<Routes>
  <Route element={<Layout/>}>

    <Route path="/" element={<Home/>}/>

    <Route path="host" element={<HostLayout />}>
      <Route index element={<Dashboard />} />
      <Route path="income" element={<Income />} />
      <Route path="vans" element={<Vans />} />
      <Route path="vans/:id" element={<VanDetailed/>}>
        <Route index element={<Detailed/>}/>
        <Route path="pricing" element={<Pricing/>}/>
        <Route path="photos" element={<Photos/>}/>
      </Route>
      <Route path="reviews" element={<Reviews />} />
    </Route>

    <Route path="about" element={<About/>}/>

    
  </Route>
</Routes>
```


- Outlet

'context' is used to pass the data
```
<Outlet context={{ product }}/>
```

'useOutletContext' is used to get the context data <br>
```
const {product} = useOutletContext()
```

- Link
- NavLink


### Hooks
- useParams
- useSearchParams
- useOutletContext

