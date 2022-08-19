# Meta Pebble-Testing
*Network: IoTeX Testnet*

**1. Download/Install**
- iOS Testflight
- ioPay: build > 21
- Android https://metapebble.s3.ap-east-1.amazonaws.com/meta-pebble/meta-pebble-v0.3.apk


**2. Create Pebble**<br/>
If you initialize the APP for the first time, click 'Get Started' and Meta Pebble will automatically create a new IMEI and SN.<br/>
The IMEI and SN is tied to the mobile, never changed after created.<br/>

<img src="https://user-images.githubusercontent.com/83109624/181507511-8c961ce6-1e69-4ef9-ab13-a620d2aa4b54.png" width="300" height="550" /><br/>

**3. Connect Wallet**<br/>
Click ‘Connect wallet’ to connect to ioPay wallet (if you use Android for testing and cannot jump to ioPay, you need to go to the settings center to cancel the original "default" wallet).<br/>

<img src="https://user-images.githubusercontent.com/83109624/181508210-d5d14d90-14a6-48fd-bfbe-e210ce476442.png" width="300" height="550" /><br/>

**4. Active Device**<br/>
Click the Activate button, and pebble will open iopay to execute the relevant contract methods.<br/>
<img src="https://user-images.githubusercontent.com/83109624/181509048-cbc493da-ebb6-4b47-916f-3550dfafff11.png" width="300" height="580" /><br/>

**5. Register**<br/>
After completing the register action, the pebble app will query the status of device, which may be slow.<br/>
<img src="https://user-images.githubusercontent.com/83109624/181510380-3b3204a0-0e29-4e4c-b30b-7cd810604097.png" width="300" height="580" /><br/>

**6. Upload Data to Server**<br/>
- Turn on the button and enter the setting, toggle the GPS and select the interval
- Open the pebble in the home screen, the GPS data will be uploaded to the server repeatedly\
<img src="https://user-images.githubusercontent.com/83109624/179714275-d2674e77-d648-4089-8b2b-783bf25dd61e.png" width="300" height="550" /><br/>
<img src="https://user-images.githubusercontent.com/83109624/179714309-6e2f9d79-dfcf-4c13-a631-8a69d7c9e561.png" width="300" height="550" /><br/>

**7. Edit Server**<br/>
Meta Pebble supports HTTPS protocol & WEBSOCKET protocol. You can switch between these two protocols in the Settings page and customize the server, or use the default server.<br/>
<img src="https://user-images.githubusercontent.com/83109624/179890611-d69e7eb7-1a9b-44f7-9c68-be93344ce42c.png" width="300" height="550" /><br/>

**8. Check GPS**<br/>
Pebble will upload your GPS data to the portal and you can check your GPS data on the web and map.\
https://w3w3bstream-example.onrender.com/

# How Developers Query MetaPebble Service?
Permission Settings (WIP)
- Developers will register with MetaPebble service and get an app token.
- Every query needs an app token to identify the app.
- An app can only query data under users' permission.
- User will give permission on a permission setting website on MetaPebble.
Create App
1. Go to https://w3bstream-oauth.onrender.com/secrets
2. Create app via input name and logo url
3. Get the app secret
![image](https://user-images.githubusercontent.com/83109624/185610506-3e28f5b0-728d-4cce-8bbb-99aae5122448.png)
Query data via app secret
1. Go to https://graphiql-online.com and using graphql api endpoint(https://dev.metapebble.app/v1/graphql)
2. Use the app secret to query data
![image](https://user-images.githubusercontent.com/83109624/185610534-b93e3bcd-6529-4ab3-ad1a-4b5301f1950b.png)
**Example query**
```
query {
  oauth_client_user_permission{
                user_id
    devices{
      deviceRecords{
        latitude
        longitude
      }
    }
  }
}
```
