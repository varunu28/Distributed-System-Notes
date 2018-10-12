# HTTP & Rest

## Web Services

 - Web service is a method of communication between two machines in a network
 - APIs that are typically accessed via HTTP protocol & executed on a remote server
 - The client communicates with server through a protocol i.e. a pre-defined set of rules. HTTP is dominant protocol in web world
 - A web client can access a Web Resource(Any type of file) through a web server
 - Each resource is identified by a unique URL
```
http://www.helloworld.com/customers/names/1

http is protocol
www.helloworld.com is the web server
customers/names/1 is path of the resource int the web server
```
 - Any kind of operation on a resource by a client is done through a request-response mechanism with each request-response pair is called a transaction
 - Due to the request-response mechanism HTTP is called a stateless system i.e. each request is individual and has enough information to fulfil the operation

## Difference between SOAP & REST

 - Soap is XML based message protocol whereas REST is architectural style protocol
 - Soap uses WSDL for communication whereas REST uses XML or JSON for communication
 - Soap invokes services by calling RPC methods whereas REST services are via URL path
 - Soap responses are not readable whereas REST returns response in a human-readable format
 - Soap uses other protocols also besides HTTP whereas REST primarily uses HTTP

## REST (Representational State Transfer)

 - A style of software architecture for distributed hypermedia systems
 - REST Triangle:
    - Nouns (Resources via URI which are non-constrained)
    - Verbs (GET, POST, DELETE which are constrained)
    - Content Types (XML, JSON which are constrained)
 - Everything is a resource. Resources are identified by the URI. Multiple URIs can refer to same resource
 - Hypermedia as the Engine of application state (HATEOAS) responses can have hypermedia links to further resources

## REST Contraints

 - Client Server
    - Clients are not responsible for activities like managing resources on database
    - Separation of concerns by dividing responsibilities between clients & servers
    - Servers are not responsible for maintaining client's state

 - Stateless
    - Servers should be stateless to improve scalability
    - Session state is maintained on the client
    - Request should have all the information to satisfy the request

 - Cacheable
    - REST clients and network intermediaries are allowed to cache
    - Server response should indicate whether or not they are cacheable and the caching period

 - Layered Systems
    - Support routing requests through network intermediaries during transit to destination server
    - Intermediaries can add value such as load balancing or local caching

 - Uniform Interface
    - Standard by which REST clients and servers commnunicate
 
 - Code on demand
    - Server can return code which will be executed on client side (Flash Applications)

## Operation Mapping
HTTP Verb | CRUD
--- | --- 
POST | Create
GET | Read
PUT | Update
DELETE | Delete

## HTTP Verbs
 - GET retrives a representation of resource from server. It is repeatable & returns HTTP 200 for successful response
 - HEAD is useful for looking up resources, data size, and content type before GETing actual resources. It is same as GET without a response body
 - POST creates a new resource on a server. The server chooses the URI.  Typically has an empty body for a successful POST request and HTTP 201
 - PUT upates/overwrites an exisiting resource and need to know the resource URI. Server returns 204
 - DELETE removes the resource and is repeatable
 - OPTION discovers allowed HTTP methods on a resource and is repeatablei

## Connectedness - HATOES
 - A logical extension of hypertext- audio, video, hyperlinks
 - Links & forms inside hypertext representation
 - Document contains URI or hyperlink that points to another resource or another possible state of application

## Conditional GET
 - Allows server & client to work together to save bandwidth & latency 
 - Client can send a condition of IF-MODIFIED-SINCE based on the timestamp and server will send a 304 (Not Modified Header) with empty body
 - The timestamp is called ETag and is useful if server application supports versioning in data store

## Partial GET
 - Only fetches a subset of a representation of a resource
 - Sends RANGE parameter in request header with byte range
 - Server returns 206 partial content 
 - Useful for resuming interrupted downloads and rendering the content while downloading remaining content
 - Example: In case of YouTube skip content

## Compression
 - To save bandwidth representations can be compressed to a fraction of original size
 - In case client is a browser then compression is already supported

## Asynchronous Operations
 - Unlike normal requests, asynchronous request does not block the client for the request to get processed. The client can make the request in an asynchronous manner and continue working on other tasks
 - This helps in prevention of wasting of computation time and thread sitting idle

## Batch Operations
 - Multiple requests can be merged into one request which in turn would automatically split into individual requests
 - Example: https://www.example.com/customer/1;customer/2;customer/3;customer/4
