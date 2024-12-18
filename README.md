# Assetto Corsa Python Documentation

## Importing the `ac` Module
The `ac` module provides various functions to retrieve information and interact with the game. Below is the documentation for the available functions.

---

### `ac.getCarState(<CAR_IDENTIFIER>, <INFO_IDENTIFIER>, [<OPTIONAL_IDENTIFIER>])`
Retrieves the type of information specified by `<INFO_IDENTIFIER>` for the car identified by `<CAR_IDENTIFIER>`.  
The `<OPTIONAL_IDENTIFIER>` is optional and used for specific data, such as tire-related information. If required, it can be one of the following:

| **Identifier**   | **Description**          |
|-------------------|--------------------------|
| **FL**           | Front Left               |
| **FR**           | Front Right              |
| **RL**           | Rear Left                |
| **RR**           | Rear Right               |

---

### **Scalar Values Returned by `<INFO_IDENTIFIER>`**
- **SpeedMS**: Current speed in meters per second `[0, …]`.
- **SpeedMPH**: Current speed in miles per hour `[0, …]`.
- **SpeedKMH**: Current speed in kilometers per hour `[0, …]`.
- **Gas**: Pressure on the gas pedal `[0, 1]`.
- **Brake**: Pressure on the brake pedal `[0, 1]`.
- **Clutch**: Pressure on the clutch pedal `[0, 1]`.
- **Gear**: Current gear `[0, max gear]`.
- **BestLap**: Best lap time in milliseconds `[0, …]`.
- **CGHeight**: Height of the car's center of gravity from the ground `[0, …]`.
- **DriftBestLap**: Best lap points in drift mode `[0, …]`.
- **DriftLastLap**: Last lap points in drift mode `[0, …]`.
- **DriftPoints**: Current lap points in drift mode `[0, …]`.
- **DriveTrainSpeed**: Speed delivered to the wheels `[0, …]`.
- **RPM**: Engine's revolutions per minute `[0, …]`.
- **InstantDrift**: Current drift points in drift mode `[0, …]`.
- **IsDriftInvalid**: Validity of the current drift in drift mode `{0, 1}`.
- **IsEngineLimiterOn**: Engine limiter status `{0, 1}`.
- **LapCount**: Current session lap count `[0, …]`.
- **LapInvalidated**: Whether the current lap is invalidated (e.g., by going off-track) `{0, 1}`.
- **LapTime**: Current lap time in milliseconds `[0, …]`.
- **LastFF**: Last force feedback signal sent to the wheel `[0, …]`.
- **LastLap**: Last lap time in milliseconds `[0, …]`.
- **NormalizedSplinePosition**: Position of the car on the track, normalized `[0, 1]`.
- **PerformanceMeter**: Projection of how many seconds the current time is from the best lap `[0, …]`.
- **Steer**: Radians of steering rotation `[-2π, 2π]`.
- **TurboBoost**: Turbo gain on engine torque for specific vehicles `[0, …]`.
- **Caster**: Caster angle in radians.

---

### **3D Vector Values Returned by `<INFO_IDENTIFIER>`**
3D vectors are represented as components `(x, y, z)`:

- **AccG**: Gravity acceleration on the vehicle's center of gravity.
- **LocalAngularVelocity**: Angular velocity of the car, using the car as the origin.
- **LocalVelocity**: Velocity relative to the car as the origin.
- **SpeedTotal**: All speed representations: `x = kmh`, `y = mph`, `z = ms`.
- **Velocity**: Current velocity vector.
- **WheelAngularSpeed**: Current wheel angular speed.
- **WorldPosition**: Current car coordinates on the map.

---

### **4D Vector Values Returned by `<INFO_IDENTIFIER>`**
4D vectors are represented as components `(w, x, y, z)`:

- **CamberRad**: Camber angle in radians for each tire.
- **CamberDeg**: Camber angle in degrees for each tire.
- **SlipAngle**: Slip angle between desired and actual direction of the vehicle `[0, 360]`, in degrees.
- **SlipRatio**: Slip ratio of the tires `[0, 1]`.
- **Mz**: Self-aligning torque.
- **Load**: Current load on each tire.
- **TyreRadius**: Radius of any tire.
- **NdSlip**, **TyreSlip**, **Dy**: Current tire properties.
- **CurrentTyresCoreTemp**: Core temperature of the tires in °C.
- **ThermalState**: Current temperature of the tires in °C.
- **DynamicPressure**: Current pressure of the tires in psi.
- **TyreLoadedRadius**: Radius of the tire under load.
- **SuspensionTravel**: Suspension vertical travel.
- **TyreDirtyLevel**: Quantity of dirt on the tires `[0, 10)`.

---

### **Wheel-Related 3D Vectors**
When combined with `<OPTIONAL_IDENTIFIER>` (e.g., **FL**, **FR**, **RL**, **RR**), these return 3D vectors `(x, y, z)`:

- **TyreContactNormal**: Normal vector to the tire's contact point.
- **TyreContactPoint**: Tire's contact point with the tarmac.
- **TyreHeadingVector**: Tire heading vector.
- **TyreRightVector**: Tire right vector.

---

### General Info:

- `ac.getDriverName(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns the driver's name of the `<CAR_ID>` car. Returns `-1` on failure.
- `ac.getTrackName(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns the track's name where `<CAR_ID>` is running. Returns `-1` on failure.
- `ac.getTrackConfiguration(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns the track’s configuration where `<CAR_ID>` is running. Returns `-1` on failure.
- `ac.getCarName(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns the car’s name of the `<CAR_ID>` car. Returns `-1` on failure.
- `ac.getLastSplits(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns a list of the car’s last splits of the `<CAR_ID>` car. Returns `-1` on failure.
- `ac.isCarInPitline(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns `1` if the car is currently in the Pitline.
- `ac.isCarInPit(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns `1` if the car is currently in the Pitbox.
- `ac.isConnected(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns `1` if the car is currently connected.
- `ac.getCarBallast(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns the ballast value of the car.
- `ac.getCarMinHeight(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns the minimum height of the car.
- `ac.getServerName()`:  
   Returns the name of the joined server.
- `ac.getServerIP()`:  
   Returns the IP of the joined server.
- `ac.getServerHttpPort()`:  
   Returns the Http port of the joined server.
- `ac.getServerSlotsCount()`:  
   Returns the total number of occupied slots in the server.
- `ac.getCarsCount()`:  
   Returns the session’s max number of cars.
- `ac.getCarLeaderboardPosition(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns position of the car on the leaderboard.
- `ac.getCarRealTimeLeaderboardPosition(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns position of the car in real-time.
- `ac.getCarFFB()`:  
   Returns the FFB Gain value for the player’s current car.
- `ac.setCarFFB(<VALUE>)`:  
   `<VALUE>` is the value that will be added to the current FFB gain.

---

### Camera Management:

- `ac.setCameraMode(<INFO_IDENTIFIER>)`:  
   `<INFO_IDENTIFIER>` can be `Cockpit`, `Car`, `Drivable`, `Track`, `Helicopter`, `OnBoard`, `Free`, `RandomImageGenerator`, `CameraStart`.
- `ac.getCameraMode()`:  
   Returns the current camera mode.
- `ac.isCameraOnBoard(<CAR_ID>)`:  
   `<CAR_ID>` must be the car ID, 0 for the player’s car. Returns `1` on success, `-1` otherwise.
- `ac.setCameraCar(<CAMERA_ID>, <CAR_ID>)`:  
   `<CAMERA_ID>` must be the F6 camera index, `<CAR_ID>` must be the car ID, 0 for the player’s car.
- `ac.getCameraCarCount(<CAR_ID>)`:  
   Returns the number of F6 cameras for the specified car.
- `ac.focusCar(<CAR_ID>)`:  
   Focuses on the specified car.

---

### Debug:

- `ac.log(<VALUE>)`:  
   `<VALUE>` must be a string. Use to send some text to the AC log file. Returns `1` on success.
- `ac.console(<VALUE>)`:  
   `<VALUE>` must be a string. Use to send a string to the AC console. Returns `1` on success.

---
## General App Management

### `ac.newApp(<VALUE>)`
- `<VALUE>`: Must be a string.
- Creates a new app and returns the corresponding identifier.
- Returns the App ID on success, `-1` otherwise.

---

### `ac.setTitle(<CONTROL_IDENTIFIER>, <TITLE>)`
- `<TITLE>`: Must be a string.
- `<CONTROL_IDENTIFIER>`: Must be a form.
- Sets the title of the specified app by `<CONTROL_IDENTIFIER>`.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setSize(<CONTROL_IDENTIFIER>, <WIDTH>, <HEIGHT>)`
- `<WIDTH>`, `<HEIGHT>`: Must be floating point numbers.
- Sets the size of the control specified by `<CONTROL_IDENTIFIER>`.
- Returns `1` on success, `-1` otherwise.

---

### `ac.addLabel(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a string.
- Adds a label to the window specified by `<CONTROL_IDENTIFIER>`.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setPosition(<CONTROL_IDENTIFIER>, <X>, <Y>)`
- `<X>`, `<Y>`: Must be floating point numbers.
- Sets the control's position specified by `<CONTROL_IDENTIFIER>` in the app.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setIconPosition(<CONTROL_IDENTIFIER>, <X>, <Y>)`
- `<X>`, `<Y>`: Must be floating point numbers.
- `<CONTROL_IDENTIFIER>`: Must be a form.
- Sets the new icon’s position inside the app.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setTitlePosition(<CONTROL_IDENTIFIER>, <X>, <Y>)`
- `<X>`, `<Y>`: Must be floating point numbers.
- `<CONTROL_IDENTIFIER>`: Must be a form.
- Sets the new title’s position inside the app.
- Returns `1` on success, `-1` otherwise.

---

### `ac.getPosition(<CONTROL_IDENTIFIER>)`
- `<CONTROL_IDENTIFIER>`: The identifier of a control.
- Returns the position as a Python tuple `(x, y)` on success, `-1` otherwise.

---

### `ac.setText(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a string.
- Sets the text of the control specified by `<CONTROL_IDENTIFIER>`.
- Returns `1` on success, `-1` otherwise.

---

### `ac.getText(<CONTROL_IDENTIFIER>)`
- `<CONTROL_IDENTIFIER>`: The control from which to get the text.
- Returns the text of the control on success, `-1` otherwise.

---

### `ac.setBackgroundOpacity(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a floating point value between `0` and `1`.
- Sets the alpha channel (opacity) of the desired control.
- Returns `1` on success, `-1` otherwise.

---

### `ac.drawBackground(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be `0` (transparent) or `1` (visible).
- Sets the background visibility of the control.
- Returns `1` on success, `-1` otherwise.

---

### `ac.drawBorder(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be `0` (no border) or `1` (draw border).
- Sets whether to draw the border of the desired control.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setBackgroundTexture(<CONTROL_IDENTIFIER>, <PATH>)`
- `<PATH>`: Starts from Assetto Corsa root folder.
- Sets the background texture of the control specified by `<CONTROL_IDENTIFIER>`.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setFontAlignment(<CONTROL_IDENTIFIER>, <ALIGNMENT>)`
- `<ALIGNMENT>`: Can be one of the following:
  - `"left"`
  - `"right"`
  - `"center"`
- Sets the font alignment of the control text.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setBackgroundColor(<CONTROL_IDENTIFIER>, <R>, <G>, <B>)`
- `<R>`, `<G>`, `<B>`: Color components (Red, Green, Blue).
- Sets the background color of the window as specified by the `<R>`, `<G>`, `<B>` values.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setVisible(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be `0` (hidden) or `1` (visible).
- Controls the visibility of the object.
- Returns `1` on success, `-1` otherwise.

---

### `ac.addOnAppActivatedListener(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a function name defined inside the Python script.
- Sets the callback function for when the app is activated.
- Returns `1` on success, `-1` otherwise.

---

### `ac.addOnAppDismissedListener(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a function name defined inside the Python script.
- Sets the callback function for when the app is dismissed.
- Returns `1` on success, `-1` otherwise.

---

### `ac.addRenderCallback(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a function name defined inside the Python script.
- Sets the callback function for the finished rendering event.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setFontColor(<CONTROL_IDENTIFIER>, <R>, <G>, <B>, <A>)`
- `<CONTROL_IDENTIFIER>`: Must be a Control identifier.
- `<R>`, `<G>`, `<B>`, `<A>`: Color values scaled from 0 to 1.
- Sets the font color of the control.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setFontSize(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: The font size to be applied.
- Sets the font size of the control's text.
- Returns `1` on success, `-1` otherwise.

---

### `ac.initFont(0, <FONTNAME>, <ITALIC>, <BOLD>)`
- Initializes a font with the specified name, italic, and bold options.
- `<FONTNAME>`: The name of the font (must be stored in `content/fonts`).
- `<ITALIC>`: `True` or `False`.
- `<BOLD>`: `True` or `False`.
- This function should be called during the app initialization.
- Returns `1` on success, `-1` otherwise.

---

### `ac.setCustomFont(<CONTROL_IDENTIFIER>, <FONTNAME>, <ITALIC>, <BOLD>)`
- `<CONTROL_IDENTIFIER>`: The control that owns the font.
- `<FONTNAME>`: Must be the name of the base font (real name, not filename, e.g., "Arial").
- `<ITALIC>`: Must be `0` for non-italic font or `1` for italic font (instance will be "Arial Italic").
- `<BOLD>`: Must be `0` for non-bold font or `1` for bold font (instance will be "Arial Bold" or "ArialItalic Bold" if italic).
- Creates or replaces the font of a control.
- The font must be saved in the `content/fonts` folder.
- Returns `1` on success, `-1` otherwise.


---

## Specific Control Management

### Button

#### `ac.addButton(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a string.
- `<CONTROL_IDENTIFIER>`: Must be a form.
- Adds a button to the window specified by `<CONTROL_IDENTIFIER>`.
- Returns the Button ID on success, `-1` otherwise.

---

#### `ac.addOnClickedListener(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a function name defined in the script.
- Associates the button with an event to trigger when it is clicked.
- Returns `1` on success, `-1` otherwise.

---

### Graph

#### `ac.addGraph(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a string.
- Adds a graph to the window specified by `<CONTROL_IDENTIFIER>`.
- Returns the Graph ID on success, `-1` otherwise.

---

#### `ac.addSerieToGraph(<CONTROL_IDENTIFIER>, <R>, <G>, <B>)`
- `<R>`, `<G>`, `<B>`: Must be floating point numbers between `0` and `1`.
- Adds a series of points to the graph, with the color specified by `<R>`, `<G>`, and `<B>`.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.addValueToGraph(<CONTROL_IDENTIFIER>, <SERIE_INDEX>, <VALUE>)`
- `<SERIE_INDEX>`: The series ID in the graph where `<VALUE>` will be added.
- Adds a value to a specific series in the graph.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.setRange(<CONTROL_IDENTIFIER>, <MIN_VALUE>, <MAX_VALUE>, <MAX_POINTS>)`
- `<MIN_VALUE>`, `<MAX_VALUE>`, `<MAX_POINTS>`: Must be floating point numbers.
- Specifies the range and maximum number of points for the graph.
- Returns `1` on success, `-1` otherwise.

---

### Spinner

#### `ac.addSpinner(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a string.
- Adds a spinner control.
- Returns the Spinner ID on success, `-1` otherwise.

---

#### `ac.setRange(<CONTROL_IDENTIFIER>, <MIN_VALUE>, <MAX_VALUE>)`
- `<MIN_VALUE>`, `<MAX_VALUE>`: Must be floating point numbers.
- Sets the min and max values of the spinner control.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.setValue(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a floating point number.
- Sets the "value" parameter of the spinner (or other controls like Progress Bar, Check Box).
- Returns `1` on success, `-1` otherwise.

---

#### `ac.getValue(<CONTROL_IDENTIFIER>)`
- Returns the current "value" parameter of the specified control (Spinner, Progress Bar, Check Box, etc.).
- Returns the value on success, `-1` otherwise.

---

#### `ac.setStep(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<CONTROL_IDENTIFIER>`: Must be a Spinner ID.
- `<VALUE>`: Must be a floating point number.
- Sets the step value for the spinner control (used for incrementing/decrementing).
- Returns `1` on success, `-1` otherwise.

---

#### `ac.addOnValueChangeListener(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a function name defined inside the script.
- Sets the callback function for when the spinner value changes.
- Returns `1` on success, `-1` otherwise.

---

### ListBox

#### `ac.getListBoxSize(<CONTROL_IDENTIFIER>)`
- `<CONTROL_IDENTIFIER>`: Must be a ListBox identifier.
- Returns the size of the List Box on success, `-1` otherwise.

---

#### `ac.setItemNumberPerPage(<CONTROL_IDENTIFIER>, <NUMBER>)`
- `<CONTROL_IDENTIFIER>`: Must be a ListBox identifier.
- `<NUMBER>`: Number of elements to be displayed per page in the ListBox.
- Sets the number of elements displayed for each page in a List Box.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.highlightListBoxItem(<CONTROL_IDENTIFIER>, <ID>)`
- `<CONTROL_IDENTIFIER>`: Must be a ListBox identifier.
- `<ID>`: Element to be selected.
- Sets the item with `<ID>` as selected in the ListBox.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.addOnListBoxSelectionListener(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a function name defined in the script.
- `<CONTROL_IDENTIFIER>`: Must be a ListBox identifier.
- Sets the callback function for item selection in a ListBox.
- The callback function receives the item's NAME and its ID (position inside the list).
- Returns `1` on success, `-1` otherwise.

---

#### `ac.addOnListBoxDeselectionListener(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a function name defined in the script.
- `<CONTROL_IDENTIFIER>`: Must be a ListBox identifier.
- Sets the callback function for item deselection in a ListBox.
- The callback function receives the item's NAME and its ID (position inside the list).
- Returns `1` on success, `-1` otherwise.

---

#### `ac.setAllowDeselection(<CONTROL_IDENTIFIER>, <ALLOW_DESELECTION>)`
- `<CONTROL_IDENTIFIER>`: Must be a ListBox identifier.
- `<ALLOW_DESELECTION>`: Must be `0` or `1`.
- If `1`, allows deselection of an item when clicked.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.setAllowMultiSelection(<CONTROL_IDENTIFIER>, <ALLOW_MULTI_SELECTION>)`
- `<CONTROL_IDENTIFIER>`: Must be a ListBox identifier.
- `<ALLOW_MULTI_SELECTION>`: Must be `0` or `1`.
- If `1`, allows multiple selections in the ListBox.
- Returns `1` on success, `-1` otherwise.


## Notes
- The functions described above modify various aspects of controls in the app.
- The `<CONTROL_IDENTIFIER>` is required to reference specific controls in your application.
- The `<VALUE>` arguments for most functions are integers or strings that specify the desired state or attribute for the control.

---
### Check Box

#### `ac.addCheckBox(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<CONTROL_IDENTIFIER>`: Must be a form.
- `<VALUE>`: Must be the form’s name.
- Adds a checkbox to the current form passed as `<CONTROL_IDENTIFIER>`.
- Returns the checkbox created on success, `-1` otherwise.

---

#### `ac.addOnCheckBoxChanged(<CONTROL_IDENTIFIER>, <VALUE>)`
- `<VALUE>`: Must be a function name defined inside the Python script.
- `<CONTROL_IDENTIFIER>`: Must be a CheckBox identifier.
- Sets the callback function for the CheckBox selection or deselection.
- The callback function receives the CheckBox's NAME and its value (1 if selected, -1 otherwise).
- Returns `1` on success, `-1` otherwise.

---

### Text Box

#### `ac.addTextBox(<CONTROL_IDENTIFIER>, <NAME>)`
- `<CONTROL_IDENTIFIER>`: Form identifier.
- `<NAME>`: Text box name.
- Adds a text box (scrollable if the text is longer than the text box) to the current form.
- **Note**: THIS CONTROL IS NOT CURRENTLY WORKING YET, so no set text has been exposed.

---

### Graphics and Rendering

#### `ac.newTexture(<PATH>)`
- `<PATH>`: Must be a string. The path is considered from the AC installation directory.
- Loads the texture specified by the given path into memory.
- Returns the texture identifier on success, `-1` otherwise.

---

#### `ac.glBegin(<PRIMITIVE_ID>)`
- `<PRIMITIVE_ID>`: Must be an integer corresponding to the following values:
  - `0`: Draw lines
  - `1`: Draw line strip
  - `2`: Draw triangles
  - `3`: Draw quads
- Begins drawing the specified primitive.
- Returns `1` on success, `-1` otherwise.

### Graphics and Rendering (Continued)

#### `ac.glBegin(<PRIMITIVE_ID>)`
- `<PRIMITIVE_ID>`: Must be an integer corresponding to the following values:
  - `0`: Draw lines
  - `1`: Draw line strip
  - `2`: Draw triangles
  - `3`: Draw quads
- Begins rendering the specified primitive.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.glEnd(void)`
- Finishes the render of a previously specified primitive.
- Returns `1` on success.

---

#### `ac.glVertex2f(<X>, <Y>)`
- `<X>`, `<Y>`: Must be floating-point numbers.
- Adds a 2D point to the rendering queue.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.glColor3f(<R>, <G>, <B>)`
- `<R>`, `<G>`, `<B>`: RGB coordinates scaled from `0` to `1`, must be floating-point numbers.
- Sets the current rendering color to the specified RGB values.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.glColor4f(<R>, <G>, <B>, <A>)`
- `<R>`, `<G>`, `<B>`: RGB coordinates scaled from `0` to `1`.
- `<A>`: Alpha component from `0` to `1` (transparency).
- Sets the current rendering color to the specified RGB values with transparency.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.glQuad(<X>, <Y>, <WIDTH>, <HEIGHT>)`
- `<X>`, `<Y>`, `<WIDTH>`, `<HEIGHT>`: Must be floating-point numbers.
- Draws a quad quickly without using `glBegin` or `glEnd`.
- Returns `1` on success, `-1` otherwise.

---

#### `ac.glQuadTextured(<X>, <Y>, <WIDTH>, <HEIGHT>, <TEXTURE_ID>)`
- `<X>`, `<Y>`, `<WIDTH>`, `<HEIGHT>`: Must be floating-point numbers.
- `<TEXTURE_ID>`: ID of the texture previously loaded.
- Draws a textured quad quickly without using `glBegin` or `glEnd`.
- Returns `1` on success, `-1` otherwise.


## Example Usage

Here is an example of how you might use the functions provided:

```python
import ac

car_id = 0  # Player's car
if ac.isConnected(car_id):
    print(f"Speed: {ac.getCarState(car_id, 'SpeedKMH')}")
    print(f"RPM: {ac.getCarState(car_id, 'RPM')}")
