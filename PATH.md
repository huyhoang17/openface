FYI: See (here)[https://medium.com/@ageitgey/machine-learning-is-fun-part-4-modern-face-recognition-with-deep-learning-c3cffc121d78] for more infomations


Pose detection and alignment
---

./util/align-dlib.py ./training-images/ align outerEyesAndNose ./aligned-images/ --size 96

==> New dir: ./aligned-images/


Generate the representations from the aligned images
---

./batch-represent/main.lua -outDir ./generated-embeddings/ -data ./aligned-images/

==> New dir: ./generated-embeddings/


Train your face detection model
---

./demos/classifier.py train ./generated-embeddings/

==> New file: ./generated-embeddings/classifier.pkl


Unknown face
---

./demos/classifier.py infer ./generated-embeddings/classifier.pkl your_test_image.jpg


output
```
=== /test-images/will-ferrel-1.jpg ===
Predict will-ferrell with 0.73 confidence.
```