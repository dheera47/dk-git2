1. copy and paste your Logs for 20 epochs, observed 99.44 in 18th epoch

Train on 60000 samples, validate on 10000 samples
Epoch 1/20

Epoch 00001: LearningRateScheduler setting learning rate to 0.005.
60000/60000 [==============================] - 32s 539us/step - loss: 0.2016 - acc: 0.9365 - val_loss: 0.0630 - val_acc: 0.9810
Epoch 2/20

Epoch 00002: LearningRateScheduler setting learning rate to 0.0037907506.
60000/60000 [==============================] - 27s 454us/step - loss: 0.0774 - acc: 0.9767 - val_loss: 0.0718 - val_acc: 0.9789
Epoch 3/20

Epoch 00003: LearningRateScheduler setting learning rate to 0.0030525031.
60000/60000 [==============================] - 28s 466us/step - loss: 0.0616 - acc: 0.9812 - val_loss: 0.0362 - val_acc: 0.9896
Epoch 4/20

Epoch 00004: LearningRateScheduler setting learning rate to 0.002554931.
60000/60000 [==============================] - 31s 516us/step - loss: 0.0538 - acc: 0.9834 - val_loss: 0.0371 - val_acc: 0.9883
Epoch 5/20

Epoch 00005: LearningRateScheduler setting learning rate to 0.0021968366.
60000/60000 [==============================] - 31s 514us/step - loss: 0.0453 - acc: 0.9858 - val_loss: 0.0298 - val_acc: 0.9904
Epoch 6/20

Epoch 00006: LearningRateScheduler setting learning rate to 0.0019267823.
60000/60000 [==============================] - 29s 475us/step - loss: 0.0421 - acc: 0.9876 - val_loss: 0.0307 - val_acc: 0.9912
Epoch 7/20

Epoch 00007: LearningRateScheduler setting learning rate to 0.0017158545.
60000/60000 [==============================] - 27s 450us/step - loss: 0.0376 - acc: 0.9881 - val_loss: 0.0271 - val_acc: 0.9923
Epoch 8/20

Epoch 00008: LearningRateScheduler setting learning rate to 0.0015465512.
60000/60000 [==============================] - 27s 454us/step - loss: 0.0346 - acc: 0.9889 - val_loss: 0.0262 - val_acc: 0.9919
Epoch 9/20

Epoch 00009: LearningRateScheduler setting learning rate to 0.0014076577.
60000/60000 [==============================] - 27s 456us/step - loss: 0.0327 - acc: 0.9897 - val_loss: 0.0231 - val_acc: 0.9929
Epoch 10/20

Epoch 00010: LearningRateScheduler setting learning rate to 0.0012916559.
60000/60000 [==============================] - 27s 446us/step - loss: 0.0289 - acc: 0.9908 - val_loss: 0.0197 - val_acc: 0.9937
Epoch 11/20

Epoch 00011: LearningRateScheduler setting learning rate to 0.0011933174.
60000/60000 [==============================] - 25s 410us/step - loss: 0.0283 - acc: 0.9908 - val_loss: 0.0279 - val_acc: 0.9919
Epoch 12/20

Epoch 00012: LearningRateScheduler setting learning rate to 0.0011088933.
60000/60000 [==============================] - 24s 408us/step - loss: 0.0265 - acc: 0.9917 - val_loss: 0.0263 - val_acc: 0.9929
Epoch 13/20

Epoch 00013: LearningRateScheduler setting learning rate to 0.0010356255.
60000/60000 [==============================] - 24s 404us/step - loss: 0.0252 - acc: 0.9917 - val_loss: 0.0229 - val_acc: 0.9933
Epoch 14/20

Epoch 00014: LearningRateScheduler setting learning rate to 0.0009714397.
60000/60000 [==============================] - 24s 406us/step - loss: 0.0245 - acc: 0.9922 - val_loss: 0.0207 - val_acc: 0.9942
Epoch 15/20

Epoch 00015: LearningRateScheduler setting learning rate to 0.0009147457.
60000/60000 [==============================] - 24s 408us/step - loss: 0.0219 - acc: 0.9931 - val_loss: 0.0230 - val_acc: 0.9933
Epoch 16/20

Epoch 00016: LearningRateScheduler setting learning rate to 0.0008643042.
60000/60000 [==============================] - 25s 422us/step - loss: 0.0232 - acc: 0.9925 - val_loss: 0.0242 - val_acc: 0.9928
Epoch 17/20

Epoch 00017: LearningRateScheduler setting learning rate to 0.000819135.
60000/60000 [==============================] - 24s 404us/step - loss: 0.0214 - acc: 0.9930 - val_loss: 0.0204 - val_acc: 0.9938
Epoch 18/20

Epoch 00018: LearningRateScheduler setting learning rate to 0.0007784524.
60000/60000 [==============================] - 25s 410us/step - loss: 0.0196 - acc: 0.9939 - val_loss: 0.0231 - val_acc: 0.9944
Epoch 19/20

Epoch 00019: LearningRateScheduler setting learning rate to 0.0007416197.
60000/60000 [==============================] - 24s 403us/step - loss: 0.0202 - acc: 0.9933 - val_loss: 0.0232 - val_acc: 0.9928
Epoch 20/20

Epoch 00020: LearningRateScheduler setting learning rate to 0.000708115.
60000/60000 [==============================] - 24s 402us/step - loss: 0.0186 - acc: 0.9941 - val_loss: 0.0208 - val_acc: 0.9938
<keras.callbacks.History at 0x7f6f8ab70e10>




2. copy and paste the result of your model.evaluate (on test data)

score = model.evaluate(X_test, Y_test, verbose=0)
print(score)

[0.02083208598219644, 0.9938]




3. strategy you have taken to achieve the said results
a. Decreased number of kernel per layer, as we need to meet the restriction of parameters.
	a1. Tried to increase the kernels layer by layer before Maxpoling. Followed from the lecture for 400x400, we need to meet 512.
b. Added Batch normalisation at every step to increase the accuracy.
c. Added dropout to decrease the difference in test and training accuracy. (Done due to overfitting after step b)
	c1. Observed the accuracy variation by changing the dropout value and came up with the final values
d. Increased the learning rate from 0.03 to 0.05 to meet the accuracy.

Considerations : Disabled the bias during each convolution and did not use FC (Fully connected)

