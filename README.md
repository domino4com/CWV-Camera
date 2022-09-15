# Using the Camera on The Extended Core (CWV)
Instead of listing a complete example here, you will find the changes below to the existing Camera Example in Arduino already. This way when the Camera Example is updated, this example will not be outdated. It also very specifically show what is different from the existing example.

## WARNING
- The Camera cannot be used at the same time as the **Neopixel** is being used. The camera and the Neopixel share a pin (18). Special attention to the code to switch between the two has to be incorporated. Only from version 4.00 on the Extended Core.
- The Camera cannot be used at the same time as the **SD Card** is being used. The camera and the SD Card's Chip Select share a pin (5). Special attention to the code to switch between the two has to be incorporated.

## The Arduino Example
- [Insert a compatible camera](#camera).
- Open the Example: File :point_right: Examples :point_right: ESP32 (Under `Examples for ESP32`...) :point_right: Camera :point_right: CameraWebServer
- Find this line `#define CAMERA_MODEL_WROVER_KIT // Has PSRAM` and comment it out. [See Screenshots](#code-changes)
- Find this line `//#define CAMERA_MODEL_AI_THINKER // Has PSRAM` and uncomment it. [^pins]
- Find this line `const char* ssid = "*********";`  and change the asterisks to your WiFi SSID.
- Find this line `const char* password = "*********";` and change the asterisks to your WiFi password.
- Choose "Huge APP..."[^board] in Partition Scheme. 
- Enable PSRAM[^board] and Upload!
- Turn on your serial monitor and you  will see something like this
```
.......
WiFi connected
Camera Ready! Use 'http://192.168.4.154' to connect
```

- Copy and paste the link, in this example `http://192.168.4.154` to your browser
- You should see something like this :point_right: `Before`
- Set an appropriate image size and click on `Start Stream`
- And you should see what your camera sees :point_right: `After`
<table>
  <tr><td>Before</td><td>After</td></tr>
<tr><td><img src="assets/stopped.png"/></td><td>
<img src="assets/started.png" /></td></tr>
  </table>
  
### Code Changes
<table>
  <tr><td>Before</td><td>After</td></tr>
<tr><td><img src="assets/before.png" /></td><td>
<img src="assets/after.png" /></td></tr>
  </table>

## Camera
### OV2640
The most wellknown camera used here is the OV2640. Here is a pair on [Amazon](https://www.amazon.com/dp/B097SZBV7N) for ~$9. I prefer the ones with a longer flat cable allowing me to position it without restricting the setup of the electronics, such as [this one](https://www.amazon.com/dp/B08XLWLGG6), but shop around.
### Insert Camera

<table>
<tbody width="600" valign="top">
  <tr>
    <th width="200">Step 1</th>
    <th width="200">Step 2</th>
    <th width="200">Step 3</th>
  </tr>
  <tr>
    <td width="200">Open the camera connector by lifting the black bar up so it is 90º to its original position.</td>
    <td width="200">Slide the camera cable into the connector with the <i>gold fingers</i> facing down and the black bar facing up.</td>
    <td width="200">Close the camera connector.</td>
  </tr>
  <tr>
    <td align="center"><img src="assets/IMG_4984.jpg" width="200" /></td>
    <td align="center,top"><img src="assets/IMG_4985.jpg" width="200" /></td>
    <td align="center"><img src="assets/IMG_4986.jpg" width="200" /></td>
  </tr>
</tbody>
</table>

[^pins]: The Extended Core uses the same pins for the camera as the ESP32-CAM from Ai-Thinker. You can see the exact pins in the [CWV GitHub Repo](https://github.com/domino4com/CWV#camera)

[^board]: The extended core has 4Mb of PSRAM, but you have to enable it: Tools :point_right: PSRAM :point_right: Enabled
![PSRAM](assets/PSRAM.png)
