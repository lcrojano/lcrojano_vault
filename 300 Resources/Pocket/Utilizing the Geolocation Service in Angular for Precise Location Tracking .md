---
url: https://blog.stackademic.com/utilizing-the-geolocation-service-in-angular-for-precise-location-tracking-b73821e995dd
readlater:
  id: "3958236952"
  provider: pocket
  synchtime: 1699293693202
---
# **Utilizing the Geolocation Service in Angular for Precise Location Tracking**

[

![Astrit Shuli](https://miro.medium.com/v2/resize:fill:88:88/1*6LE4DCjTIgvrMAOPRdp_4Q.png)









](https://astritshuli.medium.com/?source=post_page-----b73821e995dd--------------------------------)[

![Stackademic](https://miro.medium.com/v2/resize:fill:48:48/1*U-kjsW7IZUobnoy1gAp1UQ.png)











](https://blog.stackademic.com/?source=post_page-----b73821e995dd--------------------------------)

[Astrit Shuli](https://astritshuli.medium.com/?source=post_page-----b73821e995dd--------------------------------)

·

[Follow](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fsubscribe%2Fuser%2Fcfc4465f97fe&operation=register&redirect=https%3A%2F%2Fblog.stackademic.com%2Futilizing-the-geolocation-service-in-angular-for-precise-location-tracking-b73821e995dd&user=Astrit+Shuli&userId=cfc4465f97fe&source=post_page-cfc4465f97fe----b73821e995dd---------------------post_header-----------)

Published in

[

Stackademic

](https://blog.stackademic.com/?source=post_page-----b73821e995dd--------------------------------)

·

3 min read

·

6 days ago

[

](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fvote%2Fstackademic%2Fb73821e995dd&operation=register&redirect=https%3A%2F%2Fblog.stackademic.com%2Futilizing-the-geolocation-service-in-angular-for-precise-location-tracking-b73821e995dd&user=Astrit+Shuli&userId=cfc4465f97fe&source=-----b73821e995dd---------------------clap_footer-----------)

--

1

[](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fbookmark%2Fp%2Fb73821e995dd&operation=register&redirect=https%3A%2F%2Fblog.stackademic.com%2Futilizing-the-geolocation-service-in-angular-for-precise-location-tracking-b73821e995dd&source=-----b73821e995dd---------------------bookmark_footer-----------)

Listen

Share

Utilizing the Geolocation Service in Angular for Precise Location Tracking. Photo Credits: Astrit Shuli

Location-based services have become a fundamental part of modern web and mobile applications. Whether you’re building a weather app, a ride-sharing platform, or any other service that requires geospatial data, knowing the user’s location is often crucial. In this article, we will explore how to leverage the Geolocation API in an Angular application for accurate location tracking.

## **Angular and Geolocation:**

Angular, a popular web application framework, provides a robust environment for developing location-aware applications. By utilizing the Geolocation API, we can access a user’s current location with ease.

## Setting Up the Geolocation Service:

Let’s start by creating an Angular service to handle geolocation. We’ll call it the “GeolocationService.” Below is the code for the service:

import { Injectable } from '@angular/core';  
import { Observable } from 'rxjs';  
  
@Injectable({  
  providedIn: 'root',  
})  
export class GeolocationService {  
  getCurrentPosition(): Observable<any> {  
    return new Observable((observer) => {  
      if ('geolocation' in navigator) {  
        navigator.geolocation.getCurrentPosition(  
          (position) => {  
            observer.next(position);  
            observer.complete();  
          },  
          (error) => {  
            observer.error(error);  
          }  
        );  
      } else {  
        observer.error('Geolocation is not available in this browser.');  
      }  
    });  
  }  
}

In this service, we define a method called “getCurrentPosition,” which returns an Observable. This method checks if the geolocation feature is available in the user’s browser and then retrieves the current position.

## Using the Geolocation Service in an Angular Component:

Now, let’s see how to use the “GeolocationService” in an Angular component. In the component, we will call the “getCurrentPosition” method to obtain the user’s latitude and longitude. Here’s the code for the component:

import { Component, OnInit } from '@angular/core';  
import { GeolocationService } from './geolocation.service';  
  
@Component({  
  selector: 'app-geolocation',  
  templateUrl: './geolocation.component.html',  
  styleUrls: ['./geolocation.component.css']  
})  
export class GeolocationComponent implements OnInit {  
  constructor(private geolocationService: GeolocationService) {}  
  
  ngOnInit(): void {  
    this.getGeoLocation();  
  }  
  
  getGeoLocation() {  
    this.geolocationService.getCurrentPosition().subscribe({  
      next: (position) => {  
        console.log('Latitude:', position.coords.latitude);  
        console.log('Longitude:', position.coords.longitude);  
      },  
      error: (error) => {  
        console.error('Error getting geolocation:', error);  
      },  
    });  
  }  
}

In this component, we import the “GeolocationService” and call the “getCurrentPosition” method within the “getGeoLocation” function. When the user’s geolocation data is available, we log the latitude and longitude to the console. If any errors occur during the geolocation request, we log the error message.

Geolocation Allow Tracking

# Conclusion:

By implementing this geolocation service, you can create engaging applications that provide users with relevant and location-specific information, enhancing the overall user experience. Whether you’re building a map-based application, a location-based recommendation system, or any other geo-aware service, this geolocation service in Angular is a valuable tool in your development toolkit.

# Stackademic

_Thank you for reading until the end. Before you go:_

- _Please consider_ **_clapping_** _and_ **_following_** _the writer! 👏_
- _Follow us on_ [**_Twitter(X)_**](https://twitter.com/stackademichq)_,_ [**_LinkedIn_**](https://www.linkedin.com/company/stackademic)_, and_ [**_YouTube_**](https://www.youtube.com/c/stackademic)**_._**
- _Visit_ [**_Stackademic.com_**](http://stackademic.com/) _to find out more about how we are democratizing free programming education around the world._