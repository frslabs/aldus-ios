# ALDUS IOS SDK
![version](https://img.shields.io/badge/version-v1.0.0-blue)

Aldus SDK is a **Peer-to-peer**, **Feature-rich**, **Realtime** Identity Verification Solution through Video Chat. 

The Video Customer Identification Process (V-CIP) can be integrated into your existing App flow and connects to the Aldus Web Client. 

Available features
- Secure and Live P2P Video Chat with recording
- Screen Sharing
- Face & ID Capture
- Geo-Tagging
- Anti-Spoof Liveliness check

# Table Of Content

- [Prerequisite](#prerequisite)
- [iOS SDK Requirements](#ios-sdk-requirements)
- [Setup](#setup)
  - [Permissions](#permissions)
- [Installation](#installation)
  - [Using pod](#using-pod)
- [Quick Start](#quick-start)
  - [Invoking the Aldus SDK](#invoking-the-aldus-sdk)
  - [Handling the result](#handling-the-result)
- [Aldus Result](#aldus-result)
- [Aldus Error Codes](#aldus-error-codes)
- [Aldus Parameters](#aldus-parameters)
- [Help](#help)

## Prerequisite

The Aldus iOS SDK communicates with its web counterpart, the Aldus Web Client. Make sure to have integrated the Aldus Web Client so that a Peer-to-peer connection can be established.

You will need a valid license to use the Aldus SDK, which can be obtained by contacting `support@frslabs.com` . Once you have the license , follow the below instructions for a successful integration of Aldus SDK onto your iOS Application.

## iOS SDK Requirements

- iOS 10.0+
- Xcode 11.2

## Setup

#### Permission

In Info.plist file add following code to allow your application to access iPhone's camera:
``<key>NSCameraUsageDescription</key>
	<string>Aldus needs access to your camera to initiate the video call and verify your identity. It is completely private and secure with end to end encryption.</string> ``

``<key>NSMicrophoneUsageDescription</key>
	<string>Aldus uses your microphone to enable audio visual call with a Bank Official. It is completely private and secure with end to end encryption.</string>``
	
``<key>NSLocationAlwaysAndWhenInUseUsageDescription</key>
	<string>This allows Aldus to verify your physical location per Reserve Bank of Inida norms. This check is essential to proceed with the Video KYC.</string> ``
	
``<key>NSLocationWhenInUseUsageDescription</key>
	<string>This allows Aldus to verify your physical location per Reserve Bank of Inida norms. This check is essential to proceed with the Video KYC.</string>``


## Installation

#### Using Pods
You can use [CocoaPods](http://cocoapods.org/) to install `Aldus` by adding it to your `Podfile`:

```ruby
platform :ios, '11.0'
source 'https://gitlab.com/frslabs-public/ios/aldus.git'
source 'https://github.com/CocoaPods/Specs.git'
use_frameworks!
pod 'Aldus','1.0.0'
pod 'GoogleWebRTC', '1.1.28913'
pod 'Starscream', '3.0.2'
pod 'Zip'
```

## Quick Start

#### Invoking the Aldus SDK

```swift
import Aldus

Aldus.performSegueToFrameworkVC(caller: self, licenceKey: "licence_key", serverUrl: aldus_url)

```
#### Handling the result

```swift

class ViewController: UIViewController, AldusResultDelegate {

    func didReceiveAldusResult(_ data: AldusResult) {
        let sessionId = data.sessionId
        print("AldusResult -> ",sessionId)
    }
    
    func didFailedAldusResult(_ error: String) {
        print("AldusError: ", error)
    }
 }   
```


## Aldus Result

The result is obtained through the `AldusResult` object

Given below is the Result classes in brief.
<div>
<table style="width:100%">
 <tr>
 <th bgcolor="#F1F1F1" colspan="3">Public Methods</th>
 </tr>
 <tr>
 <td>String</td>
 <td>getSessionId()</td>
 <td>Returns the Session Id</td>
 </tr>
</table>
</div>

## Aldus Error Codes

Error codes and their meaning are tabulated below

| Label          | Code |Message                 |
| -------------- | ----- |---------------------- |
| ERROR_CODE_PERMISSION | 1000 | Required permissions for Aldus SDK were not granted |
| ERROR_CODE_EXPIRED_LICENSE | 1001 | Aldus SDK License has expired |
| ERROR_CODE_INVALID_LICENSE | 1002 | Invalid Aldus SDK License |
| ERROR_CODE_INVALID_CONFIG | 1003 | Invalid Aldus SDK Config |
| ERROR_CODE_NETWORK_ERROR | 1100 | Network Error |
| ERROR_CODE_INTERRUPTED | 1200 | Aldus SDK Interrupted |
| ERROR_CODE_DENIED_LOCATION | 1201 | User denied enabling location |
| ERROR_CODE_OUT_OF_COUNTRY | 1202 | User's location was found to be outside the country |

## Aldus Parameters

- `Pass licence key as a paramenter`   ***(Required)***
  
  Accepts the Aldus licence key as a `String`

  
- `Pass Aldus server url`   ***(Required)***
  
  Sets the `aldus_url` , required for networking inside the Aldus SDK

## Help
For any queries/feedback , contact us at `support@frslabs.com` 
