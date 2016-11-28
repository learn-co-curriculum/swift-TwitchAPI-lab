# Twitch

![](http://i.imgur.com/hha3yzN.jpg?1)

Twitch.tv is a web-site / app where you can watch people play video games LIVE.



# Instructions

Create a `TwitchClient.swift` file. In this file, create a struct named `Twitch`. Create a **type** property on the `Twitch` struct named `baseURL` of type `String` and give it the following default value:

```swift
https://api.twitch.tv/kraken
```

This structure will be able to make multiple `get` requests. But.. we're not going to build out separate functions for each and every `get` request we want to make. We're going to build out one function that can handle it all (based upon the arguments that will be passed to this function when it's called).

As it stands, we have created a type variable that should return back to us the value `https://api.twitch.tv/kraken`.

Writing `Twitch.baseURL` in our code will return back to us the `String` value `https://api.twitch.tv/kraken` 

---

Below this struct, lets create an extension on `URL`. Within that extension, create a static function named `twitchURL(withEndpoint:)` that takes in one argument named `endPoint` of type `String`. This function should return back a `URL`. Within the implmenetation of this function, it should 


```swift
extension URL {
    
    static func twitchURL(withEndpoint endpoint: String) -> URL {
        return URL(string: Twitch.baseURL + endpoint)!
    }
    
}
```



```swift
struct Twitch {
    
    fileprivate static let baseURL: String = "https://api.twitch.tv/kraken"
    
    func get(request: TwitchRequest, handler: @escaping ([Stream]?) -> Void) {
        let urlRequest = generateURLRequest(with: request.url)
        let urlSession = generateURLSession()
        
        generateJSON(withSession: urlSession, request: urlRequest) { json in
            guard let json = json else { handler(nil); return }
            // TODO: Based upon type of TwitchRequest", create necessary structures and pass along to handler.
            print(json)
        }
    }
    
}
```


<a href='https://learn.co/lessons/TwitchApiLab' data-visibility='hidden'>View this lesson on Learn.co</a>
