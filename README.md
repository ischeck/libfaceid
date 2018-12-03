# libfaceid for Face Recognition
<p>
    <b> FaceRecognition Made Easy.</b> libfaceid is a Python library for facial recognition that seamlessly integrates multiple face detection and face recognition models.
</p>
<p>
    <b> From Zero to Hero.</b> Learn the basics of Face Recognition and experiment with different models.
    libfaceid enables beginners to learn various models and simplifies prototyping of facial recognition solutions by providing different models to choose from.
    Multiple models for detection and encoding/embedding including classification models are supported.
    The models are seamlessly integrated so that user can mix and match detection models.
    Each model differs in speed, accuracy, memory requirements and 3rd-party library dependencies.
    This enables users to easily experiment with various solutions appropriate for their specific use cases and system requirements.
</p>
<p>
    <b> Awesome Design.</b> The library is designed so that it is easy to use, modular and robust.
    Selection of model is done via the constructors while the expose function is simply detect() or estimate() making usage very easy.
    The files are organized into modules so it is very intuitive to understand and debug.
    The robust design allows supporting new models in the future to be very easy.
</p> 
<p>
    <b> Have Some Fun.</b> In addition, the library also contains models for predicting face pose, age, gender and emotion.
    Web app is supported for some test applications using Flask so you would be able to view the video capture remotely on another computer in the same network via a web browser. 
</p>

![](https://github.com/richmondu/libfaceid/blob/master/libfaceid.jpg)
![](https://github.com/richmondu/libfaceid/blob/master/libfaceid2.jpg)
![](https://github.com/richmondu/libfaceid/blob/master/libfaceid3.jpg)


### Compatibility:

<p>
    The library and example applications have been tested on Raspberry Pi 3B+ (Python 3.5.3) and Windows 7 (Python 3.6.6)
    using <b>OpenCV</b> 3.4.3, <b>Tensorflow</b> 1.8.0 and <b>Keras</b> 2.0.8. For complete dependencies, refer to requirements.txt. 
    Tested with built-in laptop camera and with a Logitech C922 Full-HD USB webcam.
</p>


### Supported Models:

libfaceid supports the following models below. You can mix and match the models for your specific use-case and system requirements. 

#### Face Detector models for detecting face locations
- [Haar Cascade Classifier via OpenCV](https://github.com/opencv/opencv/blob/master/samples/python/facedetect.py)
- [Histogram of Oriented Gradients (HOG) via DLIB](http://dlib.net/face_detector.py.html)
- [Deep Neural Network via DLIB](http://dlib.net/cnn_face_detector.py.html)
- [Single Shot Detector with ResNet-10 via OpenCV](https://github.com/opencv/opencv/blob/3.4.0/samples/dnn/resnet_ssd_face_python.py)
- [Multi-task Cascaded CNN (MTCNN) via Tensorflow](https://github.com/ipazc/mtcnn/blob/master/tests/test_mtcnn.py)

#### Face Encoder models for generating face embeddings on detected faces
- [Local Binary Patterns Histograms (LBPH) via OpenCV](https://www.python36.com/face-recognition-using-opencv-part-3/)
- [OpenFace via OpenCV](https://www.pyimagesearch.com/2018/09/24/opencv-face-recognition/)
- [ResNet via DLIB](http://dlib.net/face_recognition.py.html)

#### Classifier models for face embedding classification to identify the face
- [Naïve Bayes](https://www.analyticsvidhya.com/blog/2017/09/naive-bayes-explained/)
- Linear SVM
- RVF SVM
- Nearest Neighbors
- Decision Tree
- Random Forest
- Neural Net
- Adaboost
- QDA

#### Other models can be integrated to libfaceid in the future.
- FaceNet (Inception ResNet v1) via Tensorflow https://github.com/davidsandberg/facenet
  Refer to my fork for instructions on how to use FaceNet https://github.com/richmondu/facenet/tree/master/usage
- VGG-Face (VGG-16, ResNet-50) via Keras https://github.com/rcmalli/keras-vggface
- OpenFace via Torch and Lua https://github.com/cmusatyalab/openface

#### Additional models (bonus features for marketability): 
- Face Pose estimator models for predicting face landmarks <b>(face landmark detection)</b>
- Face Age estimator models for predicting age <b>(age detection)</b>
- Face Gender estimator models for predicting gender <b>(gender detection)</b>
- Face Emotion estimator models for predicting facial expression <b>(emotion detection)</b>


### Usage:

#### Installation:

        1. Install Python 3 and Python PIP
           Use Python 3.5.3 for Raspberry Pi 3B+ and Python 3.6.6 for Windows
        2. Install the required Python PIP package dependencies
           pip install -r requirements.txt
           

#### Pre-requisites:

        1. Add the dataset of images under the datasets directory
           The datasets folder should be in the same location as the test applications.
           Having more images per person makes accuracy much better.
           If only 1 image is possible, then do data augmentation.
             Example:
             datasets/rico - contain .jpeg images of person name rico
             datasets/coni - contain .jpeg images of person named coni 
             ...
             datasets/xyz - contain .jpeg images of person named xyz 
        2. Train the model using the datasets. 
           Can use facial_recognition_training.py
           Make sure the models used for training is the same for actual testing for better accuracy.


#### Examples:

        detector models:       0-HAARCASCADE, 1-DLIBHOG, 2-DLIBCNN, 3-SSDRESNET, 4-MTCNN
        encoder models:        0-LBPH, 1-OPENFACE, 2-DLIBRESNET
        classifier algorithms: 0-NAIVE_BAYES, 1-LINEAR_SVM, 2-RBF_SVM, 3-NEAREST_NEIGHBORS, 4-DECISION_TREE, 
                               5-RANDOM_FOREST, 6-NEURAL_NET, 7-ADABOOST, 8-QDA
        camera resolution:     0-QVGA, 1-VGA, 2-HD, 3-FULLHD

        1. facial_recognition_training.py
            Usage: python facial_recognition_training.py --detector 0 --encoder 0 --classifier 0
        2. facial_recognition_testing_image.py
            Usage: python facial_recognition_testing_image.py --detector 0 --encoder 0 --image datasets/rico/1.jpg

        3. facial_recognition_testing_webcam.py
            Usage: python facial_recognition_testing_webcam.py --detector 0 --encoder 0 --webcam 0 --resolution 0
        4. facial_recognition_testing_webcam_flask.py
            Usage: python facial_recognition_testing_webcam_flask.py
                   Then open browser and type http://127.0.0.1:5000 or http://ip_address:5000

        5. facial_estimation_poseagegenderemotion_webcam.py
            Usage: python facial_estimation_poseagegenderemotion_webcam.py --detector 0 --webcam 0 --resolution 0
        6. facial_estimation_poseagegenderemotion_webcam_flask.py
            Usage: python facial_estimation_poseagegenderemotion_webcam_flask.py
                   Then open browser and type http://127.0.0.1:5000 or http://ip_address:5000


#### Training models with dataset of images:

        from libfaceid.detector import FaceDetectorModels, FaceDetector
        from libfaceid.encoder  import FaceEncoderModels, FaceEncoder
        from libfaceid.classifier  import FaceClassifierModels

        INPUT_DIR_DATASET         = "datasets"
        INPUT_DIR_MODEL_DETECTION = "models/detection/"
        INPUT_DIR_MODEL_ENCODING  = "models/encoding/"
        INPUT_DIR_MODEL_TRAINING  = "models/training/"

        face_detector = FaceDetector(model=FaceDetectorModels.DEFAULT, path=INPUT_DIR_MODEL_DETECTION)
        face_encoder = FaceEncoder(model=FaceEncoderModels.DEFAULT, path=INPUT_DIR_MODEL_ENCODING, path_training=INPUT_DIR_MODEL_TRAINING, training=True)
        face_encoder.train(face_detector, path_dataset=INPUT_DIR_DATASET, verify=verify, classifier=FaceClassifierModels.NAIVE_BAYES)


#### Face Recognition on images:

        import cv2
        from libfaceid.detector import FaceDetectorModels, FaceDetector
        from libfaceid.encoder  import FaceEncoderModels, FaceEncoder

        INPUT_DIR_MODEL_DETECTION = "models/detection/"
        INPUT_DIR_MODEL_ENCODING  = "models/encoding/"
        INPUT_DIR_MODEL_TRAINING  = "models/training/"

        image = cv2.VideoCapture(imagePath)
        face_detector = FaceDetector(model=FaceDetectorModels.DEFAULT, path=INPUT_DIR_MODEL_DETECTION)
        face_encoder = FaceEncoder(model=FaceEncoderModels.DEFAULT, path=INPUT_DIR_MODEL_ENCODING, path_training=INPUT_DIR_MODEL_TRAINING, training=False)

        frame = image.read()
        faces = face_detector.detect(frame)
        for (index, face) in enumerate(faces):
            (x, y, w, h) = face
            face_id, confidence = face_encoder.identify(frame, (x, y, w, h))
            label_face(frame, (x, y, w, h), face_id, confidence)
        cv2.imshow(window_name, frame)
        cv2.waitKey(5000)

        image.release()
        cv2.destroyAllWindows()


#### Real-Time Face Recognition w/a webcam:

        import cv2
        from libfaceid.detector import FaceDetectorModels, FaceDetector
        from libfaceid.encoder  import FaceEncoderModels, FaceEncoder

        INPUT_DIR_MODEL_DETECTION = "models/detection/"
        INPUT_DIR_MODEL_ENCODING  = "models/encoding/"
        INPUT_DIR_MODEL_TRAINING  = "models/training/"

        camera = cv2.VideoCapture(webcam_index)
        face_detector = FaceDetector(model=FaceDetectorModels.DEFAULT, path=INPUT_DIR_MODEL_DETECTION)
        face_encoder = FaceEncoder(model=FaceEncoderModels.DEFAULT, path=INPUT_DIR_MODEL_ENCODING, path_training=INPUT_DIR_MODEL_TRAINING, training=False)

        while True:
            frame = camera.read()
            faces = face_detector.detect(frame)
            for (index, face) in enumerate(faces):
                (x, y, w, h) = face
                face_id, confidence = face_encoder.identify(frame, (x, y, w, h))
                label_face(frame, (x, y, w, h), face_id, confidence)
            cv2.imshow(window_name, frame)
            cv2.waitKey(1)

        camera.release()
        cv2.destroyAllWindows()


#### Real-Time Face Pose/Age/Gender/Emotion Estimation w/a webcam:

        import cv2
        from libfaceid.detector import FaceDetectorModels, FaceDetector
        from libfaceid.pose import FacePoseEstimatorModels, FacePoseEstimator
        from libfaceid.age import FaceAgeEstimatorModels, FaceAgeEstimator
        from libfaceid.gender import FaceGenderEstimatorModels, FaceGenderEstimator
        from libfaceid.emotion import FaceEmotionEstimatorModels, FaceEmotionEstimator

        INPUT_DIR_MODEL_DETECTION       = "models/detection/"
        INPUT_DIR_MODEL_ENCODING        = "models/encoding/"
        INPUT_DIR_MODEL_TRAINING        = "models/training/"
        INPUT_DIR_MODEL_ESTIMATION      = "models/estimation/"

        camera = cv2.VideoCapture(webcam_index)
        face_detector = FaceDetector(model=FaceDetectorModels.DEFAULT, path=INPUT_DIR_MODEL_DETECTION)
        face_pose_estimator = FacePoseEstimator(model=FacePoseEstimatorModels.DEFAULT, path=INPUT_DIR_MODEL_ESTIMATION)
        face_age_estimator = FaceAgeEstimator(model=FaceAgeEstimatorModels.DEFAULT, path=INPUT_DIR_MODEL_ESTIMATION)
        face_gender_estimator = FaceGenderEstimator(model=FaceGenderEstimatorModels.DEFAULT, path=INPUT_DIR_MODEL_ESTIMATION)
        face_emotion_estimator = FaceEmotionEstimator(model=FaceEmotionEstimatorModels.DEFAULT, path=INPUT_DIR_MODEL_ESTIMATION)

        while True:
            frame = camera.read()
            faces = face_detector.detect(frame)
            for (index, face) in enumerate(faces):
                (x, y, w, h) = face
                age = face_age_estimator.estimate(frame, face_image)
                gender = face_gender_estimator.estimate(frame, face_image)
                emotion = face_emotion_estimator.estimate(frame, face_image)
                shape = face_pose_estimator.detect(frame, face)
                face_pose_estimator.add_overlay(frame, shape)
                label_face(age, gender, emotion)
            cv2.imshow(window_name, frame)
            cv2.waitKey(1)

        camera.release()
        cv2.destroyAllWindows()


### Performance Optimizations:

Speed and accuracy is often a trade-off. Performance can be optimized depending on your specific use-case and system requirements. Some models are optimized for speed while others are optimized for accuracy. Be sure to test all the provided models. Below are additional suggestions to optimize performance.

#### Speed
- Reduce the frame size for face detection.
- Perform face recognition every X frames only
- Use threading in reading camera source frames or in processing the camera frames.
- Update the library and configure the parameters directly.

#### Accuracy
- Add more datasets if possible (ex. do data augmentation). More images per person will often result to higher accuracy.
- Add face alignment if faces in the datasets are not aligned or when faces may be unaligned in actual deployment.
- Update the library and configure the parameters directly.


### Credits:

Below are links to valuable resoures. Special thanks to all of these guys for sharing their work on Face Recognition. Without them, learning Face Recognition would be difficult.
- [OpenCV tutorials by Adrian Rosebrock](https://www.pyimagesearch.com/)
- [Dlib by Davis King](https://github.com/davisking/dlib)
- [Face Recognition (Dlib wrapper) by Adam Geitgey](https://github.com/ageitgey/face_recognition)
- [FaceNet implementation by David Sandberg](https://github.com/davidsandberg/facenet)
- [OpenFace (FaceNet implementation) by Satyanarayanan](https://github.com/cmusatyalab/openface)
- [VGG-Face implementation by Refik Can Malli](https://github.com/rcmalli/keras-vggface)


### Contribute:

Have a good idea for improving libfaceid? Found a bug? Then create a new ticket. 
If you just want to chat, then message me in [twitter](https://twitter.com/richmond_umagat).
