# Meta Pebble-Testing
*Network: IoTeX Mainnet*

**1. Download/Install**
- iOS Testflight link: https://testflight.apple.com/join/CQiGu2Xc (Please open in Safari)
- ioPay: build > 21
- Android https://metapebble.s3.ap-east-1.amazonaws.com/meta-pebble/meta-pebble-release.apk


**2. Create Pebble**<br/>
If you initialize the APP for the first time, Meta Pebble will automatically create a new IMEI and SN for you.<br/>
The IMEI and SN is tied to the mobile, never changed after created.<br/>


**3. Connect Wallet**<br/>
Click '**Register Device**' to connect to your wallet (if you use Android for testing and cannot jump to ioPay, you need to go to the settings center to cancel the original 'default' wallet), currently we support ioPay and MetaMask..<br/>

<img src="https://user-images.githubusercontent.com/83109624/227508213-b7820524-8d0a-4e52-8a98-e92882614d85.png" width="300" height="580" /><br/>
<img src="https://user-images.githubusercontent.com/83109624/227510431-35a048b7-168b-4233-91ed-8d916c6a560f.png" width="300" height="580" /><br/>


**4. Active Device**<br/>
Click the '**Register**', and pebble will jump to your wallet to execute the relevant contract.<br/>
<img src="https://user-images.githubusercontent.com/83109624/186665519-2830a748-09ea-41a8-b927-2da0bb8d5768.png" width="300" height="580" /><br/>


After completing the register action, the pebble app will query the status of device, which may be slow.<br/>
<img src="https://user-images.githubusercontent.com/83109624/181510380-3b3204a0-0e29-4e4c-b30b-7cd810604097.png" width="300" height="580" /><br/>

**5. Upload Location Data to Server**<br/>
- Allow Meta Pebble to use your location data
- Turn on the button in the home screen, the GPS data will be uploaded to the server repeatedly\
<img src="https://user-images.githubusercontent.com/83109624/227514659-e056fd23-a29b-4b37-95ca-7c29090d55b3.png" width="300" height="550" /><br/>
<img src="https://user-images.githubusercontent.com/83109624/227514932-505a31a0-1456-49ff-8bd5-047514d56f72.png" width="300" height="550" /><br/>


**6. Check GPS**<br/>
Pebble will upload your GPS data to the portal and you can check your GPS data on the web and map.\
https://example.metapebble.app/


# How Developers Query MetaPebble Service?
**1. Permission Settings (WIP)**<br/>
- Developers will register with MetaPebble service and get an app token.
- Every query needs an app token to identify the app.
- An app can only query data under users' permission.
- User will give permission on a permission setting website on MetaPebble.<br/>

**2. Create App**<br/>
1. Go to https://oauth.metapebble.app/
2. Create app via input name and logo url
3. Get the app secret
![image](https://user-images.githubusercontent.com/83109624/186460155-3e250027-c721-40ae-a768-bd8d1ef08874.png)

**3. Query data via app secret**<br/>
1. Go to https://graphiql-online.com and using graphql api endpoint(https://dev.metapebble.app/v1/graphql)
2. Use the app secret to query data (authorization: Bearer ‘secret’)
![image](https://user-images.githubusercontent.com/83109624/186850829-9d2ac671-7513-41b0-899c-823465cf43f5.png)

**Example query**
```
query {
  oauth_device(limit: 20, order_by:{created_at: desc}){
    id
    owner
    deviceRecord(limit: 20, order_by:{created_at: desc}){
      latitude
      longitude
    }
  }
}
```

# How to check your devices location on the map?
1.Connect wallet which register a metapebble here: https://example.metapebble.app/<br/>
![image](https://user-images.githubusercontent.com/83109624/186666506-88645f57-a017-4510-91e1-fb0e71671df8.png)

2.Click Authorize, select Metapebble as provider.<br/>
![image](https://user-images.githubusercontent.com/83109624/186667028-f31124f4-3611-49de-9d2f-1bc8961199f3.png)
![image](https://user-images.githubusercontent.com/83109624/186667108-cb8f5a42-be12-46cf-a027-1157d960239b.png)

3.Check the uploaded data from the authorized app or your wallet on the map.<br/>

