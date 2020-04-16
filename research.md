# General Notes 

## Cloudflare Workers

https://blog.cloudflare.com/introducing-cloudflare-workers/

- Cloudflare is an HTTP clash
  - as well as a DNS / SSL protection
  - protecting against attacks
  - load balancing
  - but historically these were all fixed functions

- Cloudflare Workers allows developers to customize the way they use cloudflare platforms and networks
  - Runs Javascript V8 
  - Service Worker API

### Example Worker 

<pre><code>

// A Service Worker which skips cache if the request contains a cookie

addEventListener('fetch', event => {
  let request = event.request
  if (request.headers.has('Cookie')) {
    // Cookie present. Add Cache-Control: no-cache.
    let newHeaders = new Headers(request.headers)
    newHeaders.set('Cache-Control', 'no-cache')
    event.respondWith(fetch(request, {headers: newHeaders}))
  }

  // Use default behavior.
  return
}) </code></pre>

### Use Cases

- A "Cloudflare Worker" is JavaScript you write that runs on Cloudflare's edge.
- A "Cloudflare Service Worker" is specifically a worker which handles HTTP traffic and is written against the Service Worker API

- Can do anything, example use cases
  - Use custom logic to decide which requests are cacheable at the edge, and canonicalize them to improve cache hit rate.
  - Expand HTML templates directly on the edge, fetching only dynamic content from your server.
  - Respond to stateless requests directly from the edge without contacting your origin server at all.
  - Split one request into multiple parallel requests to different servers, then combine the responses.Enhance security
  - Implement custom security rules and filters.
  - Implement custom authentication and authorization mechanisms.
  - Deploy fast fixes to your site in seconds, without having to update your own servers.
  - Implement custom load balancing and failover logic.
  - Respond dynamically when your origin server is unreachable.

Security: The V8 JavaScript engine is arguably the most scrutinized code sandbox in the history of computing, and the Chrome security team is one of the best in the world. Moreover, Google pays massive bug bounties to anyone who can find a vulnerability. (That said, we have added additional layers of our own sandboxing on top of V8.)

Ubiquity: JavaScript is everywhere. Anyone building a web application already needs to know it: whereas their server could be written in a variety of languages, the client has to be JavaScript, because that's what browsers run.

Alternatives: Lua / Virutal Machines / Containers / Vx32 / Node.js 

## Cloudflare for Gaming

https://www.cloudflare.com/gaming/

- 100% Cloudflare uptime SLA for your custom TCP/UDP protocols and protection from DDoS attacks and abusive bots **tl;dr protection from attacks on service, 24/7**
- Supercharge game downloads and in-game performance for a faster, more real-time gamer experience **tl;dr speed of downloads, reduce lag**
- Develop bespoke serverless matchmaking architecture (and more!) without worrying about unexpected spikes in demand **tl;dr use as much computing power as you need**

### Current Users

- Nodecraft (Gaming servers for CSGO / Minecraft / Left4Dead)
- Discord (Gaming voice-communications / community chat platform)
- Turtle Entertainment (parent company of CS:GO and Dota2 tournament host)
- Curse (Owns fandom.com, gaming comunities, E-sports team)

**None of the above users are actual gaming publishers, but rather gaming adjacent, where are RIOT / EPIC / Activision-Blizzard?**

## Generic Cloudflare Research

### Glassdoor Cloudflare PM Questions 

- You are PM for a new Cloudflare product, The traditional Cloudflare products make sales reps 100,000 in commission. Your product only makes a sales rep 50,000 in commission. How do you convince the sales rep to start selling your product?  
  - 50,000 per product or over what interval of time?
  - I guess this reflects that sales at Cloudflare are handled by an external sales team and not in house?
    - but a cursory glance at the CF careers page tells me there are sales hires? 

- Name a physical product that you like, what do you like about it, how would you improve it?
  - pretty standard product question

- What is a product you would begin to work on tomorrow at Cloudflare  
  - theoretical knowledge
  - foresight into innovative things to work on in the CF suite in the future

- If you were building multi-tasking on the early iPhone, how might you go about it?  
  - Break it down, MVP, v1, v1.1 etc.
  - MVP: Basic UI to switch apps. Don't need full isolation etc. yet, could unload and load apps
  - v1.1: True multi-tasking, animated app icon scrolling
  - v1.2: Security, include live screenshot
  - Discussion of the product/feature process, and some tech details around memory isolation.

### Marketting Intern Blog

- SSL / TLS Transport Layer Security
  - cryptographic protocals which provide security 
  - handshake protocol
  - users can only see end points, but not see any inside data

- Seeing orange?
  - CND and TLS/SSL provision
  - content delivery network

- Focus on smart?