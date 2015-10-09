# TeamClutch-FTC2016
### Note that this is a development release code function and syntax is not guaranteed to be the
 same between versions and code quality may be below usual standards

## Xtensible OpMode
This is the main "OpMode" class for this library. You can extend this class for use
within the FTC SDK. It also bootstraps our library for use.

#### Core syntactical changes:
##### Getting references to robot hardware
Old Way:
```java
hardwareMap.dcMotor.get("motor_1");
```
New Way:
```java
ctx.hardwareMap().getDcMotors().get("motor_1");
```
##### Getting access to a gamepad's left joystick X
Old Way:
```java
gamepad1.left_joystick.X;
```
New Way:
```java
ctx.xGamepad1().getLeftJoystick().getX();
```

##### Logging
Old Way:
```java
RobotLog.i("Hello World!");
```
New Way:
```java
ctx.log().i("Hi", "Hello World!");
```

##### Networking
Old Way:
There was never an old way.

New Way:
```java
ctx.enableNetworking().startNetworking();
```

Modifying the server parameter:
```java
ctx.enableNetworking();
// The default web directory is "/sdcard/FIRST/web"
ctx.getServerSettings().setWebDirectory("/put/here/where/your/web/directory/is");
ctx.startNetworking();
```
### Structure
 * FtcRobotController
     - doc - Documentation for the FTC SDK are included with this repository.
        - "apk" - contains the .apk files for the FTC Driver Station and FTC Robot Controller apps.
        - "javadoc" - contains the JavaDoc user documentation for the FTC SDK.
        - "tutorial" - contains PDF files that help teach the basics of using the FTC SDK.
     - src - contains the source code for the FTC SDK user-editable code portions
        - "opmodes" - provides user-defined OpModes
 * OpModeLibrary - This module is where you add your OpMode code (note that you must not have
    dependencies on the FtcRobotController module, but you may depend on its libraries)
 * FtcXtesible - This module contains our code to help you out with your programming

### Upstream Changelog
 * New user interfaces for FTC Driver Station and FTC Robot Controller apps.
 * An init() method is added to the OpMode class.
   - For this release, init() is triggered right before the start() method.
   - Eventually, the init() method will be triggered when the user presses an "INIT" button on driver station.
   - The init() and loop() methods are now required (i.e., need to be overridden in the user's op mode).
   - The start() and stop() methods are optional.
 * A new LinearOpMode class is introduced.
   - Teams can use the LinearOpMode mode to create a linear (not event driven) program model.
   - Teams can use blocking statements like Thread.sleep() within a linear op mode.
 * The API for the Legacy Module and Core Device Interface Module have been updated.
   - Support for encoders with the Legacy Module is now working.
 * The hardware loop has been updated for better performance.

#### Authors
David Sargent, T. Eng, Jonathan Berling
August 3, 2015

