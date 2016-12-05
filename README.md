android-btxfr
=============
A lightweight library for transferring data between Android devices using Bluetooth.

Introduction
------------
android-btxfr is a lightweight library designed to send and receive any type of data between Android (API 15 and higher). It can be used to exchange text, files, photos, videos, sounds, or literally any other type of binary data. The library supports anything that can be put into a byte stream and includes digest checking to ensure data integrity.  

Building The Library
--------------------
The build.xml ANT file can be used to build the library. The resulting android-btxfr.jar can then be included as a library in any Android project.

Sample Application
------------------
[BTPhotoTransfer](http://github.com/simonguest/BTPhotoTransfer-sample) is a sample application that shows how to use the android-btxfr library. The sample application shows how to use the library to exchange photos between devices.

Using The Library
-----------------

The library assumes that devices are already paired, and does not contain any logic to create pair relationships. The library exposes two thread types (ClientThread and ServerThread) depending on whether you are sending or receiving data.

Receiving data is easy. Simply run the server thread, passing the paired bluetooth device and handler. The handler will be called with the following messages:

* *DATA_PROGRESS_UPDATE* - Data is being received by the other device.  The message contains the progress of the data.
* *DATA_RECEIVED* - Data has been fully received by the other device.  The message will contain the actual payload (a byte stream of the image, video, etc.)

There are other message types to handle failure conditions.

The client thread works in a similar fashion. Invoke the client thread, passing the paired bluetooth device and handler. The handler will be called with the following messages:

* *READY_FOR_DATA* - Indicates that the connection has been established, and data can be sent.
* *SENDING_DATA* - Indicates that data is being sent to the other device.
* *DATA_SENT_OK* - Indicates that the recipient received the payload.

Again, there are other message types to handle failures.

The sample application shows these threads, handlers, and messages in action.

License
-------

Copyright 2013 Simon Guest

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License.

You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  See the License for the specific language governing permissions and limitations under the License.
