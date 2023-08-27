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

```
const {id} = useParams()
```

- useSearchParams

It is used to set and get the search parameters
```
import { useEffect, useState } from "react"
import { Link, NavLink, useSearchParams } from "react-router-dom";

const About = () => {
  const [products, setProducts] = useState([])
  const [searchParams, setSearchParams] = useSearchParams()
  const categoryFilter = searchParams.get('category')

 

  useEffect(() => {
    fetch('https://fakestoreapi.com/products')
      .then(res=> res.json())
      .then(data=>{
        setProducts([...products, ...data])
      })
  }, []);

 

  const displayFilterData = categoryFilter ? products.filter((product => product.category === categoryFilter)) : products
  
  return (
    <div className="container">
      <p>Select by category</p>
       {/* way 1 */}
      <Link to={'.'}>all</Link><br />
      <Link to={'?category=jewelery'}>jewelery</Link><br />
      <Link to={'?category=electronics'}>electronics</Link><br />
      {/* way 2 */}
      <button onClick={()=> setSearchParams("?category=men's clothing")}>men's clothing</button>
      {/* way 3: this is the better way */}
      <button onClick={() => setSearchParams({ category: "women's clothing" })}>women's clothing</button>

      
      
      
      {/* <ul>
        <li>
          <NavLink exact to={'.'}>all</NavLink><br />
        </li>
        <li>
          <NavLink to={'?category=jewelery'}>jewelery</NavLink><br />
        </li>
        <li>
          <NavLink to={'?category=electronics'}>electronics</NavLink><br />
        </li>
      </ul> */}
      
   
      <div className="row">
        {
          displayFilterData.map((product, i) => {
            return (
              <div key={i} className="col-md-3">
                <div className="m-2 border p-3">
                  <img src={product.image} alt="" height={'100'} width={'100'} />
                  <h4>{product.title}</h4>
                  <h6 className="text-danger">{product.category}</h6>
                  <h5>$ {product.price}</h5>
                </div>
              </div>
            )
          })
        }
      </div>
    </div>
  )
}

export default About
```
- useOutletContext
- useLocation

```
const location = useLocation()
console.log(location);

hash: ""
key: "default"
pathname: "/host/vans/2"
search: ""
state: null

```

we can pass data through <Link> using location instade of useParams

set
```
<Link to="/" state={{ product }}/>
```

get
```
const location = useLocation()
console.log(location);

we will get this type of value:
hash:""
key:"jf8tybc5"
pathname:"/host/vans/1"
search:""
state:
  product: {id: 1, title: 'Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops', price: 109.95, description: 'Your perfect pack for everyday use and walks in th…to 15 inches) in the padded sleeve, your everyday', category: "men's clothing",}

now we can get this like:
location.state.product.title
```


















