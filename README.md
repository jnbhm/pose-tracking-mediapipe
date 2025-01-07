# Simple pose landmarks detection with MediaPipe

This is an example how to use the pose landmark detection model with MediaPipe. Find the full description of the model [here.](https://ai.google.dev/edge/mediapipe/solutions/vision/pose_landmarker)

To run this project you'll need to have [Node.js](https://nodejs.org/en) installed on your machine.

## [DEMO](http://pld.tdbr.xyz/)

## Dev

To start this project run the following command in the root folder of the project.

```bash
npm install
```

Run the dev task to see your changes live.

```bash
npm run dev
```

### Use the detections

To use the detection you can access the `detections` object in the `processResults` function. You can find this function in `src/js/script.js`

```javascript
function processResults(detections) {
    landmarksContainer.innerHTML = "";

    if (detections.landmarks && detections.landmarks[0]?.length) {
        // draw all keypoints
        for (let i = 0; i < detections.landmarks[0].length; i++) {
            // extract the landmark from the array
            const landmark = detections.landmarks[0][i];

            const x = videoWidth * (1 - landmark.x);
            const y = videoHeight * landmark.y;
            drawKeypoint(x, y, null);
        }
    }
}
```

### [Image of landmarks](https://ai.google.dev/static/edge/mediapipe/images/solutions/pose_landmarks_index.png)

---

## Build

To build this project run the following command:

```bash
npm run build
```

The built project will be in the `dist` folder.
