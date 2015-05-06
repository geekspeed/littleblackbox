1. **My router/VPN/printer/server/etc isn't listed in the LittleBlackBox database. Does this mean I'm safe?**

> Maybe. Maybe not. If it is not listed in the database then either it doesn't use default SSL keys or we haven't gotten around to adding them yet.

2. **My router/VPN/printer/server/etc is listed in the LittleBlackBox database. What do I do?**

> If you have the ability to change the default SSL certificates, do so immediately. If this is not possible, then treat your HTTPS sessions as if they were un-secure HTTP sessions. It may also be possible to tunnel your connections through another service, such as SSH.

3. **How did you get these SSL keys?**

> By extracting them from the device's firmware.

4. **I have a piece of software/firmware/whatever that uses default SSL keys. Can I contribute them to the LittleBlackBox project?**

> Yes! We will need you to send us a copy of the public certificate and the private key. Additionally, you will need to fill out the submission.txt template (located in the docs directory) with as much information as possible - the more the better. ZIP up these three files and send them to: littleblackbox@devttys0.com.

5. **I have hacked XYZ's server and have their SSL keys. How can I contribute them to the LittleBlackBox project?**

> You don't. We will not accept illegally obtained SSL keys.

6. **Once I have a private key, how do I decrypt and/or man-in-the-middle HTTPS sessions?**

  * Wireshark has the ability to decrypt SSL traffic (http://www.wireshark.org).
  * SSLsniff can man-in-the-middle SSL sessions (http://www.thoughtcrime.org/software/sslsniff/).

7. **I've found a bug in the LittleBlackBox utility and/or an invalid entry in the database.**

> Please report all bugs to the LittleBlackBox Google Code page: http://code.google.com/p/littleblackbox/issues/list.