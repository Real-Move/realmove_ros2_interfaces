# Real-Move ROS 2 Interfaces Catalog
This ROS 2 package contains all interfaces (messages, services, actions, etc.) related to Real-Move project.

## Actions

- `action/Calibrate.action`: Starts a calibration workflow that monitors ArUco detections until completion and reports progress.

## Services

- `srv/ResetSkeletonScaling.srv`: Requests resetting the scaling state for a specific skeleton ID and returns operation status.
- `srv/String.srv`: Sends a generic string payload to a service endpoint and receives success plus a response message.

## Messages

- `msg/Action.msg`: Represents a scored action classification for a specific skeleton over a fixed analysis window.
- `msg/ActionAnalysis.msg`: Stores the time-bounded analysis of one action repetition, including collected feedback events.
- `msg/ActionAnalysisArray.msg`: Groups multiple action analysis results in a single message.
- `msg/ActionArray.msg`: Publishes all action predictions available at a given timestamp.
- `msg/ActionFeedback.msg`: Encodes a feedback code with one or more timestamps marking when it occurred.
- `msg/ArucoMarker.msg`: Describes one detected ArUco marker using its ID and image-space corner coordinates.
- `msg/ArucoMarkerArray.msg`: Publishes all ArUco markers detected in one frame with a shared header.
- `msg/HighKneesRun.msg`: Reports step timing and knee-height metrics for a high-knees running exercise.
- `msg/Identity.msg`: Maps a numeric identity ID to a human-readable name.
- `msg/IdentityArray.msg`: Publishes a headered list of tracked identities.
- `msg/Keypoint.msg`: Represents one detected keypoint with 3D position and confidence score.
- `msg/Object.msg`: Describes a detected object with keypoints, class metadata, pose orientation, and tracking ID.
- `msg/ObjectArray.msg`: Publishes all detected objects for a frame with a common header.
- `msg/Skeleton.msg`: Contains one skeleton instance with body, hand, and face keypoint sets.
- `msg/SkeletonArray.msg`: Publishes all detected skeletons in a frame under a shared header.
- `msg/SkeletonDescriptionArray.msg`: Provides textual descriptions associated with detected skeletons.
- `msg/SkeletonJointStateArray.msg`: Publishes per-skeleton joint states as an array of `sensor_msgs/JointState`.
