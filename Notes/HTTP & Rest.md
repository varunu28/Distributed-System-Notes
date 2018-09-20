# HTTP & Rest

## Web Services

 - Web service is a method of communication between two machines in a network
 - APIs that are typically accessed via HTTP protocol & executed on a remote server

## REST (Representational State Transfer)

 - A style of software architecture for distributed hypermedia systems
 - REST Triangle:
    - Nouns (Resources via URI)
    - Verbs (GET, POST, DELETE)
    - Content Types (XML, JSON)

## REST Contraints

 - Client Server
    - Clients are not responsible for activities like managing resources on database
    - Separation of concerns by dividing responsibilities between clients & servers

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
 - HEAD is useful for looking up resources, data size, and content type before GETing actual resources
 - POST creates a new resource on a server. The server chooses the URI.  Typically has an empty body for a successful POST request and HTTP 201
 - PUT upates/overwrites an exisiting resource and need to know the resource URI. Server returns 204
 - DELETE removes the resource and is repeatable
 - OPTION discovers allowed HTTP methods on a resource and is repeatable
