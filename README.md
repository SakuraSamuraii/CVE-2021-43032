# CVE-2021-43032
In XenForo ≤ 2.2.7, a threat actor with access to the admin panel can save cross-site scripting payloads in any function within the application that accepts HTML code. A payload placed within the 'Advertising' functionality will execute globally on the client side, allowing for multiple exploitation scenarios, whereas other payloads will execute on the clientside depending on where it was stored.

Credits: John Jackson @johnjhacking & Jackson Henry @JacksonHHax
# Steps to Replicate
1. Login to the admin panel located at /admin.php
![Admin Panel](https://github.com/SakuraSamuraii/CVE-2021-43032/blob/main/1.png?raw=true)
2. Create a new advertisement and store the payload <script>alert(1)</script> within the HTML body.
![Advertisement PoC](https://github.com/SakuraSamuraii/CVE-2021-43032/blob/main/2.png?raw=true)
3. Navigate to the clientside and you'll see the alert popup universally across the application.
![Alert 1](https://github.com/SakuraSamuraii/CVE-2021-43032/blob/main/3.png?raw=true)
4. You can store scripts that will execute in varying parts of the application. As another example, here is the process of storing malicious script in the node functionality.
![Node PoC](https://github.com/SakuraSamuraii/CVE-2021-43032/blob/main/4.png?raw=true)
5. Going to the clientside and navigating to the particular node results in execution.
![Alert 2](https://github.com/SakuraSamuraii/CVE-2021-43032/blob/main/5.png?raw=true)
# Impact
The biggest risk with this vulnerability would be an ill-intended user executing covert actions embeded in extensive HTML pages, such as mining cryptocurrency or exfiltrating data. This could be a user with pre-existing access to the application, or a threat actor that obtains credentials via account takeover or social engineering methodology. 
