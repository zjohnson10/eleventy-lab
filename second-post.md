### [Return to posts page](posts)


# Back End Development with APIs

Today, I will be covering how we can extract data from an API and mapping it on the Google Maps API. I will also be covering using that data in a `wikipedia-query` tag to display a wikipedia page about such contents. 

### GeoIP
We can use an app called GeoIP, linked [here](https://freegeoip.app/json/), that can get geographical information, such as coordinates, about a device and send it back to the user as a JSON response. The response from GeoIP is based on your IP address, so if you are using a VPN it will give you the geo information of wherever your VPN is connected to and not your actual physical location. This is what the API response looks like in formatted JSON:
```
{
"ip": "104.39.60.125",
"country_code": "US",
"country_name": "United States",
"region_code": "PA",
"region_name": "Pennsylvania",
"city": "State College",
"zip_code": "16801",
"time_zone": "America/New_York",
"latitude": 40.7957,
"longitude": -77.8618,
"metro_code": 574
}
```

### Getting JSON Response Using fetch Command
We first want to establish the GeoIP API as in instance in our class constructor by saying `this.locationEndpoint = 'https://freegeoip.app/json/';`. From here we will use the fetch command and call this `locationEndpoint` in a method called getGEOIPData:

```
async getGEOIPData() {
    const IPClass = new UserIP();
    const userIPData = await IPClass.updateUserIP();
    return fetch(this.locationEndpoint + userIPData.ip)
      .then(resp => {
        if (resp.ok) {
          return resp.json();
        }
        return false;
      })
      .then(data => {
        console.log(data);
        this.long = data.longitude;
        this.lat = data.latitude;
        this.city = data.city;
        this.state = data.region_name;
        return data;
      });
  }
```
The fetch command simply stated goes to that webpage and retrieves whatever data we are telling to retrieve or whatever data the webpage has to offer. In this case, the GeoIP webpage returns a JSON response, so that response is assigned to the `data` instance we see in the `.then()` call. 

After we receive the response, we can assign that response data attributes into the attributes of our class. This is our latitude and longitude coordinates that the GeoIP API gives us assigned into `this.lat` and `this.long` respectively. 

### Using fetch response to map a location

For this next portion, we will use the Google Maps iframe API, which allows us to embed a Google Maps interactive image into our html page. We will do this in the `render()` function of our code. We define the url of the Google Maps that we will use with our `this.lat` and `this.long` coordinates from before. Then, send this url into an html tag that shows this map on our webpage. 

```
render() {
    // this function runs every time a properties() declared variable changes
    // this means you can make new variables and then bind them this way if you like
    const url = `https://maps.google.com/maps?q=${this.lat},${this.long}&t=&z=15&ie=UTF8&iwloc=&output=embed`;
    return html`<iframe title="Where you are" src="${url}"></iframe> 
  }
```

### Wiring data into a `wikipedia-query` tag
Now that we have established our ability to retrieve data from APIs using `fetch()`, we can use this data to embed a wikipedia article on our page. In order to do this, we have to import the wikipedia-query dependency into our project with:
`import '@lrnwebcomponents/wikipedia-query/wikipedia-query.js';`. From here we can embed wikipedia articles on our webpage using an html tag inside the `render()` function. 

```
<wikipedia-query search="${this.city}, ${this.state}"></wikipedia-query>
<wikipedia-query search="${this.city}"></wikipedia-query>
<wikipedia-query search="${this.state}"></wikipedia-query>`;
```
The tags above represent three different possible entries into this wikipedia-query search. The three are a city and state combination, only a city, or only a state. We used the data from the fetch command from the GeoIP API to get the current city and state we are in. In the API response, state is listed as `region_name`, so be careful when translating the response over. You should now successfully have three wikipedia articles embedded into your page. This is what one might look like:

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bg2ectipkbld9tkm494y.png)

Congratulations, you have successfully integrated two APIs into your webpage! The source code used for this project can be found [here](https://github.com/zjohnson10/ip-project/tree/master/src).


