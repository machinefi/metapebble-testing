# Meta Pebble-Testing
*Network: IoTeX Testnet*

**1. Download/Install**
- iOS Testflight
- ioPay: build > 21
- Android https://metapebble.s3.ap-east-1.amazonaws.com/meta-pebble/meta-pebble-v0.3.apk


**2. Create Pebble**<br/>
If you initialize the APP for the first time, click 'Get Started' and Meta Pebble will automatically create a new IMEI and SN.<br/>
The IMEI and SN is tied to the mobile, never changed after created.<br/>

<img src="https://user-images.githubusercontent.com/83109624/181507511-8c961ce6-1e69-4ef9-ab13-a620d2aa4b54.png" width="300" height="580" /><br/>

**3. Connect Wallet**<br/>
Click '**Active Device**' to connect to ioPay wallet (if you use Android for testing and cannot jump to ioPay, you need to go to the settings center to cancel the original 'default' wallet).<br/>

<img src="https://user-images.githubusercontent.com/83109624/186664999-c805f4e5-5d4a-4475-9cbd-0820a0d9c4c7.png" width="300" height="580" /><br/>


**4. Active Device**<br/>
Click the '**Register**', and pebble will open iopay to execute the relevant contract methods.<br/>
<img src="https://user-images.githubusercontent.com/83109624/186665519-2830a748-09ea-41a8-b927-2da0bb8d5768.png" width="300" height="580" /><br/>


After completing the register action, the pebble app will query the status of device, which may be slow.<br/>
<img src="https://user-images.githubusercontent.com/83109624/181510380-3b3204a0-0e29-4e4c-b30b-7cd810604097.png" width="300" height="580" /><br/>

**5. Upload Data to Server**<br/>
- Turn on the button and enter the setting, toggle the GPS and select the interval
- Open the pebble in the home screen, the GPS data will be uploaded to the server repeatedly\
<img src="https://user-images.githubusercontent.com/83109624/179714275-d2674e77-d648-4089-8b2b-783bf25dd61e.png" width="300" height="550" /><br/>
<img src="https://user-images.githubusercontent.com/83109624/186663774-3a3aef3a-510c-43ce-ae76-3ed4d284640f.jpg" width="300" height="550" /><br/>


**6. Edit Server**<br/>
Meta Pebble supports HTTPS protocol & WEBSOCKET protocol. You can switch between these two protocols in the Settings page and customize the server, or use the default server.<br/>
<img src="https://user-images.githubusercontent.com/83109624/186663826-c89dda6f-1aa4-4604-9fbf-d210139f4967.jpg" width="300" height="550" /><br/>


**7. Check GPS**<br/>
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
2. Use the app secret to query data
![image](https://user-images.githubusercontent.com/83109624/186458508-4ac008ab-f9cc-4d2e-87da-88675571b7a4.png)

**Tips: <br/>**
*1. Need to add '**authorization**' to Key;*<br/>
*2. Need to add '**Bearer**' before enter secret;*<br/>

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

# How to check your devices location on the map?
1.Connect wallet which register a metapebble here: https://example.metapebble.app/<br/>
![image](https://user-images.githubusercontent.com/83109624/186666506-88645f57-a017-4510-91e1-fb0e71671df8.png)

2.Click Authorize, select Metapebble as provider.<br/>
![image](https://user-images.githubusercontent.com/83109624/186667028-f31124f4-3611-49de-9d2f-1bc8961199f3.png)
![image](https://user-images.githubusercontent.com/83109624/186667108-cb8f5a42-be12-46cf-a027-1157d960239b.png)

3.Check the uploaded data from the authorized app or your wallet on the map.<br/>

