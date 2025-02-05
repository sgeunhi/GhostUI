# GhostUI: A Dataset for Predicting Hidden Interactions in Mobile Applications

## Data


### Dataset Format Documentation
- `screenshot_id`(str): unique identifier for each screenshot in UUID format 
- `name`(str): name of the mobile application 
- `category`(str): main category of the application
- `subcategory`(str): specific subcategory of the application
- `task`(str): human-readable description of the task to be performed
- `screenshot_path`(str): path to the original screenshot image file
- `annotated_screenshot_path`(str): path to the screenshot with visual annotations
- `ui_elements`(list[obj]): 
  - `element_id`(str): unique identifier for the ui element
  - `element_type`(str): type of ui element
    - `text`: text content
    - `icon`: graphical icon or button
    - `area`: interactive area or region
  - `semantic`(str): meaning or description of the element
  - `coordinate`(list[float]): normalized coordinates [x1, y1, x2, y2] representing the element's bounding box (values between 0 and 1)
  - `actionable`(bool): whether the element can be interacted with
- `hidden_interactions`(list[obj]):
  - `gesture`(str): type of gesture required
    - `tap`
    - `double_tap`
    - `long_press`
    - `swipe`
    - `pinch`
  - `target_element_id`(str): id of the ui element this interaction applies to
  - `effect`(str): description of what happens when the gesture is performed
- `metadata`(obj)
  - `resolution`(str): screen resolution in format "widthxheight"
  - `device`(str): device model
  - `os_version`(str): operating system version
 
### Dataset Example(w/ OmniParser + Single Screenshot)
```json
{
  "screenshot_id": "6c7a7082-2897-41c7-9688-4b0f3d778cdb",
  "name": "instagram",
  "category": "entertainment",
  "subcategory": "sns",
  "task" : "Leave the second chatroom.",
  "ui_elements": [
    {
      "element_id": "0",
      "element_type": "text",
      "semantic": "16:35",
      "coordinate": [0.09155556233723958, 0.019704433497536946, 0.11822222222222223, 0.02175697865353038],
      "actionalble": false
    },
     {
      "element_id": "1",
      "element_type": "icon",
      "semantic": "creating a new document or file",
      "coordinate": [0.7431111111111111, 0.027093596059113302, 0.12711111111111112, 0.02175697865353038],
      "actionalble": true
    },
    {
      "element_id": "2",
      "element_type": "area",
      "semantic": "",
      "coordinate": [0.8746666666666667, 0.02914614121510673, 0.06755555555555555, 0.01683087027914614],
      "actionable": true,
      "hidden_interaction": {
        "gesture": "long_press",
        "effect": "reveal additional options",
      }
    },
  ],
  "hidden_interactions": [
    {
      "gesture": "long_press",
      "target_element_id": "video_area",
      "effect": "2x speed playback",
    }
  ],
  "screenshot_path": "data/screenshots/youtube_0001.png",
  "annotated_screenshot_path": "data/annotated_screenshots/youtube_0001.png",
  "metadata": {
    "resolution": "1080x1920",
    "device": "Pixel 6",
    "os_version": "Android 12"
  }
}
```             
