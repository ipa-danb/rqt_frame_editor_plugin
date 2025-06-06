# ROS Services Files Documentation

---


## Available Services

| Service Name       | Description                           |
|--------------------|-------------------------------------|
| [AlignFrame.srv](#alignframe-srv)       | Align a frame relative to a source frame |
| [EditFrame.srv](#editframe-srv)         | Edit the pose of a frame                   |
| [GetFrame.srv](#getframe-srv)           | Query the `parent` frame and relative `pose` of a frame named `name`.|
| [GetFrameNames.srv](#getframenames-srv) | Get a list of frame names                  |
| [RemoveFrame.srv](#removeframe-srv)     | Remove a frame                             |
| [SetFrame.srv](#setframe-srv)            | Set or update a frame                      |
| [SetParentFrame.srv](#setparentframe-srv) | Change the parent of a frame               |
| [CopyFrame.srv](#copyframe-srv)          | Copy a frame                              |
| [LoadYaml.srv](#loadyaml-srv)            | Load frames from a YAML file               |
| [SaveYaml.srv](#saveyaml-srv)            | Save frames to a YAML file                  |

---

## AlignFrame.srv

**Request:**

```plaintext
string name
string source_name
int32 mode

# Modes (bitmask)
int32 mode_none = 0
int32 mode_x = 1
int32 mode_y = 2
int32 mode_z = 4
int32 mode_a = 8
int32 mode_b = 16
int32 mode_c = 32

int32 mode_position = 7
int32 mode_orientation = 56
int32 mode_pose = 63
```

**Response:**

```plaintext
int32 error_code
```

**Description:**  
Align a frame named `name` relative to `source_name` using the specified `mode` flags.

---

## EditFrame.srv

**Request:**

```plaintext
string name
```

**Response:**

```plaintext
int32 error_code
```

**Description:**  
Edit the `name` of a frame.

---

## GetFrame.srv

**Request:**

```plaintext
string name
```

**Response:**

```plaintext
int32 error_code
string name
string parent
geometry_msgs/Pose pose
```

**Description:**  
Query the `parent` frame and relative `pose` of a frame named `name`.  
---

## GetFrameNames.srv

**Request:**

```plaintext
```

**Response:**

```plaintext
int32 error_code
string[] names
```

**Description:**  
Get a list of all frame editor frame names.

---

## RemoveFrame.srv

**Request:**

```plaintext
string name
```

**Response:**

```plaintext
int32 error_code
```

**Description:**  
Remove the frame with the specified `name`.

---

## SetFrame.srv

**Request:**

```plaintext
string name
string parent
geometry_msgs/Pose pose
```

**Response:**

```plaintext
int32 error_code
```

**Description:**  
Set or update a frame with the given `name`, `parent`, and `pose`.

---

## SetParentFrame.srv

**Request:**

```plaintext
string name
string parent
bool keep_absolute
```

**Response:**

```plaintext
int32 error_code
```

**Description:**  
Change the parent of the frame named `name` to `parent`. `keep_absolute` indicates if the pose stays at the same position.

---

## CopyFrame.srv

**Request:**

```plaintext
string name
string parent
string source_name
```

**Response:**

```plaintext
int32 error_code
```

**Description:**  
Copy a frame from `source_name` to a new frame with `name` and `parent`.

---

## LoadYaml.srv

**Request:**  
string filename

**Response:**

```plaintext
bool success
string message
```

**Description:**  
Load frames from a YAML file with `filename`. Returns success flag and message.

---

## SaveYaml.srv

**Request:**

```plaintext
string filename
```

**Response:**

```plaintext
bool success
string message
```

**Description:**  
Save current frames to a YAML file identified by `filename`.

---