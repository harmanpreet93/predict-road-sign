## Predict the Road Sign

### [Problem Statement](https://www.hackerearth.com/problem/machine-learning/predict-the-road-sign-1/?target=_blank)

Building digital maps is challenging, and maintaining it up to date in an ever-changing world is even more challenging. Various machine learning techniques helps us to detect road signs and changes in real world, and process it to update maps.

The problem presented here is related to a step after detecting a sign on a road. This step has to now identify each road geometry on which this sign is applicable. While sounds like a simple problem, signs in junctions makes this more challenging.

For example, given a sign detected on a road from a 4-camera setting on vehicle, the closest sighting of the sign may be in the right facing camera, with a sharp sign angle with respect to the direction of the car on which cameras set is mounted. Next step for updating map using this sign is to identify the exact road on which this sign is to be placed or applied.

On a+ junction, when a sign is detected on the right camera, its hard now to tell if this sign is for the straight road, or for the right-side road, unless you consider parameters like sign bounding box aspect ratio.

For example, a sign detected from Front camera will have a natural aspect ratio of the sign when it is actually facing front of the car, however when same sign is detected on a right-side camera with a sharp angle from front, sign bounding box gets skewed, giving a hint that although its detected in right, it’s still facing the front of the car.

Dataset provided here has details on camera sign was detected, Angle of sign with respect to front in degrees, Sign's reported bounding box aspect ratio (width/height), Sign Width and Height, and the target feature Sign Facing, which is where the sign is actually facing.

Goal here is to predict where the sign is actually facing with respect to the vehicle, given above set of inputs.

[Dataset](https://github.com/harmanpreet93/predict-road-sign/tree/master/dataset/?target=_blank) 
  
  
### Data Information

| Variable | Description |
|----------|-------------|
ID | a unique identifier for each record in dataset
DetectedCamera |	imagine a car, which is fitted with 4 cameras on top, one each facing front, right, rear and left. Each cameras clicks pictures on every few meters as car moves. DetectedCamera value tells you on which camera image a road sign was observed/found, by an image detection software
AngleOfSign |	values are in degrees ranging from 0 to 360 in clockwise direction from the front of car, indicates the angle from the front of the car to the direction in which the sign is detected
SignWidth |	width of the sign bounding box in the image in pixels
SignHeight |	height of the sign bounding box in the image in pixels
SignAspectRatio |	this is the width/height ratio of the sign bounding box, derived from SignWidth/SignHeight. Can provide an indication that sign is facing camera or not. A sign facing the driver, detected on an image captured from almost 80 degrees from front (on right camera), will have a bounding box that is skewed from its original aspect ratio. If its facing the right camera, it will have nearly original aspect ratio of the sign.
SignFacing (Target)	| For the above inputs, where the sign is actually facing is captured here, from manually reviewed sign facing records


### [Submission](https://github.com/harmanpreet93/predict-road-sign/tree/master/submission/?target=_blank)

csv file with the Id and target class probabilities.

```
Id,Front, Left, Rear, Right
2c9180975a056a64015a1e10d3f270fe,0.71,.037, 0.03, 0.002
2c9180975a056a64015a1de4deb16bdc,0.41, 0.02, 0.01, 0.0001
2c9180975a056a64015a1e0e70ea70ce,0.84, 0.137, 0.04, 0.0008
2c9180975a056a64015a1dfed0c46ec6,0.03, 0.197, 0.086, 0.009
```
