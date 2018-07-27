# Fruit-Quality Android App using Tensor Flow
Android app to classify the freshness of fruits
I have used the following file to train my model by retraining the inception_v3 model based on the fruit data set created by collecting images and applied data augmentation techniques.
If you wish to train your model on a custom data set, please follow the below steps:
1)Creation of the data set
2)Use reasonable data augmentation techniques to enhance the data set.

python retrain.py --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=\<path to the data set>
  
 
retrain.py is taken from the following github link i.e https://github.com/googlecodelabs/tensorflow-for-poets-2
  
  Once the model is ready, clone the tensor flow repository locally.
  Install bazel properly in your system i.e https://docs.bazel.build/versions/master/install.html
  Use the following commands in the tensorflow repository to strip the model.
                bazel build tensorflow/python/tools:strip_unused && \
                bazel-bin/tensorflow/python/tools/strip_unused \
                --input_graph=\<path to the trained model> \
                --output_graph=\<path to the stripped_model> \
                --input_node_names=Mul \
                --output_node_names=final_result \
                --input_binary=true
  
  Then clone this repository and then perform the following actions.
  
  Update the graph and labels.txt in the assets folder with the stripped_model graph and labels.
  
  Update the paths for graph and labels.txt in the MainActivity.kt
  
  Update the input layer to "Mul" in the MainActivity.kt
  
  Detailed description is given in the following blog:
  https://medium.com/@elye.project/applying-tensorflow-in-android-in-4-steps-to-recognize-superhero-f224597eb055
  
  

