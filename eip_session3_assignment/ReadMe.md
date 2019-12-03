Base model final validation accuracy :

poch 50/50
390/390 [==============================] - 20s 52ms/step - loss: 0.3336 - acc: 0.8883 - val_loss: 0.5678 - val_acc: 0.8244
Model took 1021.55 seconds to train





My model :

# Define the model
model_new = Sequential()

model_new.add(SeparableConvolution2D(filters = 48, kernel_size=(3, 3), 
            padding = 'valid', strides = (1,1), depth_multiplier = 1, 
            input_shape = (32, 32, 3), activation='relu', use_bias=True, depthwise_initializer='glorot_uniform',
            pointwise_initializer='glorot_uniform', bias_initializer='zeros', depthwise_regularizer=None, 
            pointwise_regularizer=None, bias_regularizer=None, activity_regularizer=None,
            depthwise_constraint=None, pointwise_constraint=None, bias_constraint=None)) #output_size = 30 x 30, receptive_field = 3x3

model_new.add(BatchNormalization())

model_new.add(SeparableConvolution2D(filters = 48, kernel_size=(3, 3), 
            padding = 'valid', strides = (1,1), depth_multiplier = 1, 
            activation='relu', use_bias=True, depthwise_initializer='glorot_uniform',
            pointwise_initializer='glorot_uniform', bias_initializer='zeros', depthwise_regularizer=None, 
            pointwise_regularizer=None, bias_regularizer=None, activity_regularizer=None,
            depthwise_constraint=None, pointwise_constraint=None, bias_constraint=None)) #output_size = 28 x 28, receptive_field = 5x5

model_new.add(BatchNormalization())

model_new.add(Dropout(0.15))

model_new.add(MaxPooling2D(pool_size=(2,2))) #output_size = 14 x 14, receptive_field = 10 x 10

model_new.add(SeparableConvolution2D(filters = 96, kernel_size=(3, 3), 
            padding = 'valid', strides = (1,1), depth_multiplier = 1, 
            activation='relu', use_bias=True, depthwise_initializer='glorot_uniform',
            pointwise_initializer='glorot_uniform', bias_initializer='zeros', depthwise_regularizer=None, 
            pointwise_regularizer=None, bias_regularizer=None, activity_regularizer=None,
            depthwise_constraint=None, pointwise_constraint=None, bias_constraint=None)) #output_size = 12 x 12, receptive_field = 12 x 12

model_new.add(BatchNormalization())

model_new.add(SeparableConvolution2D(filters = 96, kernel_size=(3, 3), 
            padding = 'valid', strides = (1,1), depth_multiplier = 1, 
            activation='relu', use_bias=True, depthwise_initializer='glorot_uniform',
            pointwise_initializer='glorot_uniform', bias_initializer='zeros', depthwise_regularizer=None, 
            pointwise_regularizer=None, bias_regularizer=None, activity_regularizer=None,
            depthwise_constraint=None, pointwise_constraint=None, bias_constraint=None)) #output_size = 10 x 10, receptive_field = 14 x 14

model_new.add(BatchNormalization())

model_new.add(Dropout(0.15))

model_new.add(MaxPooling2D(pool_size=(2, 2))) #output_size = 5 x 5, receptive_field = 28 x 28


model_new.add(SeparableConvolution2D(filters = 96, kernel_size=(3, 3), 
            padding = 'valid', strides = (1,1), depth_multiplier = 1, 
            activation='relu', use_bias=True, depthwise_initializer='glorot_uniform',
            pointwise_initializer='glorot_uniform', bias_initializer='zeros', depthwise_regularizer=None, 
            pointwise_regularizer=None, bias_regularizer=None, activity_regularizer=None,
            depthwise_constraint=None, pointwise_constraint=None, bias_constraint=None)) #output_size = 3 x 3, receptive_field = 30 x 30

model_new.add(BatchNormalization())

model_new.add(SeparableConvolution2D(filters = 96, kernel_size=(3, 3), 
            padding = 'valid', strides = (1,1), depth_multiplier = 1, 
            activation='relu', use_bias=True, depthwise_initializer='glorot_uniform',
            pointwise_initializer='glorot_uniform', bias_initializer='zeros', depthwise_regularizer=None, 
            pointwise_regularizer=None, bias_regularizer=None, activity_regularizer=None,
            depthwise_constraint=None, pointwise_constraint=None, bias_constraint=None)) #output_size = 1 x 1, receptive_field = 32 x 32

model_new.add(BatchNormalization())

model_new.add(Flatten())
model_new.add(Dense(200))
model_new.add(Activation('relu'))
model_new.add(Dropout(0.1))
model_new.add(Dense(100))
model_new.add(Activation('relu'))
model_new.add(Dropout(0.1))
model_new.add(Dense(num_classes, activation='softmax'))
# Compile the model
model_new.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])






/usr/local/lib/python3.6/dist-packages/ipykernel_launcher.py:12: UserWarning: The semantics of the Keras 2 argument `steps_per_epoch` is not the same as the Keras 1 argument `samples_per_epoch`. `steps_per_epoch` is the number of batches to draw from the generator at each epoch. Basically steps_per_epoch = samples_per_epoch/batch_size. Similarly `nb_val_samples`->`validation_steps` and `val_samples`->`steps` arguments have changed. Update your method calls accordingly.
  if sys.path[0] == '':
/usr/local/lib/python3.6/dist-packages/ipykernel_launcher.py:12: UserWarning: Update your `fit_generator` call to the Keras 2 API: `fit_generator(<keras_pre..., validation_data=(array([[[..., verbose=1, steps_per_epoch=390, epochs=50)`
  if sys.path[0] == '':
Epoch 1/50
390/390 [==============================] - 49s 126ms/step - loss: 1.5462 - acc: 0.4377 - val_loss: 1.2921 - val_acc: 0.5418
Epoch 2/50
390/390 [==============================] - 28s 73ms/step - loss: 1.1744 - acc: 0.5831 - val_loss: 1.2949 - val_acc: 0.5545
Epoch 3/50
390/390 [==============================] - 28s 73ms/step - loss: 1.0306 - acc: 0.6336 - val_loss: 1.1694 - val_acc: 0.5936
Epoch 4/50
390/390 [==============================] - 28s 73ms/step - loss: 0.9195 - acc: 0.6751 - val_loss: 1.1013 - val_acc: 0.6241
Epoch 5/50
390/390 [==============================] - 29s 73ms/step - loss: 0.8449 - acc: 0.7063 - val_loss: 0.9582 - val_acc: 0.6643
Epoch 6/50
390/390 [==============================] - 29s 73ms/step - loss: 0.7817 - acc: 0.7272 - val_loss: 0.8819 - val_acc: 0.6905
Epoch 7/50
390/390 [==============================] - 28s 73ms/step - loss: 0.7456 - acc: 0.7387 - val_loss: 0.9641 - val_acc: 0.6699
Epoch 8/50
390/390 [==============================] - 28s 73ms/step - loss: 0.6979 - acc: 0.7580 - val_loss: 0.8682 - val_acc: 0.7093
Epoch 9/50
390/390 [==============================] - 28s 73ms/step - loss: 0.6710 - acc: 0.7650 - val_loss: 0.8986 - val_acc: 0.6948
Epoch 10/50
390/390 [==============================] - 29s 73ms/step - loss: 0.6408 - acc: 0.7761 - val_loss: 0.8873 - val_acc: 0.7018
Epoch 11/50
390/390 [==============================] - 28s 73ms/step - loss: 0.6129 - acc: 0.7854 - val_loss: 0.7891 - val_acc: 0.7362
Epoch 12/50
390/390 [==============================] - 28s 73ms/step - loss: 0.5923 - acc: 0.7925 - val_loss: 0.7949 - val_acc: 0.7257
Epoch 13/50
390/390 [==============================] - 28s 73ms/step - loss: 0.5723 - acc: 0.7997 - val_loss: 0.7736 - val_acc: 0.7406
Epoch 14/50
390/390 [==============================] - 28s 72ms/step - loss: 0.5503 - acc: 0.8054 - val_loss: 0.9353 - val_acc: 0.7038
Epoch 15/50
390/390 [==============================] - 29s 73ms/step - loss: 0.5336 - acc: 0.8131 - val_loss: 0.7973 - val_acc: 0.7318
Epoch 16/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5187 - acc: 0.8168 - val_loss: 0.8409 - val_acc: 0.7204
Epoch 17/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5028 - acc: 0.8225 - val_loss: 0.7932 - val_acc: 0.7371
Epoch 18/50
390/390 [==============================] - 28s 73ms/step - loss: 0.4922 - acc: 0.8244 - val_loss: 0.7388 - val_acc: 0.7513
Epoch 19/50
390/390 [==============================] - 28s 73ms/step - loss: 0.4778 - acc: 0.8297 - val_loss: 0.8458 - val_acc: 0.7304
Epoch 20/50
390/390 [==============================] - 28s 73ms/step - loss: 0.4638 - acc: 0.8353 - val_loss: 0.8073 - val_acc: 0.7368
Epoch 21/50
390/390 [==============================] - 28s 73ms/step - loss: 0.4505 - acc: 0.8401 - val_loss: 0.8263 - val_acc: 0.7336
Epoch 22/50
390/390 [==============================] - 29s 73ms/step - loss: 0.4421 - acc: 0.8426 - val_loss: 0.7669 - val_acc: 0.7561
Epoch 23/50
390/390 [==============================] - 29s 73ms/step - loss: 0.4353 - acc: 0.8460 - val_loss: 0.7125 - val_acc: 0.7657
Epoch 24/50
390/390 [==============================] - 28s 73ms/step - loss: 0.4206 - acc: 0.8496 - val_loss: 0.7555 - val_acc: 0.7601
Epoch 25/50
390/390 [==============================] - 28s 73ms/step - loss: 0.4119 - acc: 0.8529 - val_loss: 0.8373 - val_acc: 0.7375
Epoch 26/50
390/390 [==============================] - 29s 73ms/step - loss: 0.4018 - acc: 0.8578 - val_loss: 0.7713 - val_acc: 0.7497
Epoch 27/50
390/390 [==============================] - 28s 73ms/step - loss: 0.4008 - acc: 0.8567 - val_loss: 0.8036 - val_acc: 0.7510
Epoch 28/50
390/390 [==============================] - 29s 74ms/step - loss: 0.3921 - acc: 0.8591 - val_loss: 0.8213 - val_acc: 0.7478
Epoch 29/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3816 - acc: 0.8626 - val_loss: 0.7737 - val_acc: 0.7580
Epoch 30/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3717 - acc: 0.8674 - val_loss: 0.8434 - val_acc: 0.7410
Epoch 31/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3671 - acc: 0.8705 - val_loss: 0.7698 - val_acc: 0.7562
Epoch 32/50
390/390 [==============================] - 28s 73ms/step - loss: 0.3616 - acc: 0.8696 - val_loss: 0.8228 - val_acc: 0.7525
Epoch 33/50
390/390 [==============================] - 28s 73ms/step - loss: 0.3566 - acc: 0.8724 - val_loss: 0.8270 - val_acc: 0.7527
Epoch 34/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3481 - acc: 0.8750 - val_loss: 0.7928 - val_acc: 0.7572
Epoch 35/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3439 - acc: 0.8777 - val_loss: 0.7860 - val_acc: 0.7581
Epoch 36/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3343 - acc: 0.8791 - val_loss: 0.8212 - val_acc: 0.7515
Epoch 37/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3368 - acc: 0.8796 - val_loss: 0.7922 - val_acc: 0.7570
Epoch 38/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3223 - acc: 0.8830 - val_loss: 0.7859 - val_acc: 0.7663
Epoch 39/50
390/390 [==============================] - 29s 74ms/step - loss: 0.3185 - acc: 0.8847 - val_loss: 0.8389 - val_acc: 0.7520
Epoch 40/50
390/390 [==============================] - 28s 73ms/step - loss: 0.3129 - acc: 0.8872 - val_loss: 0.8037 - val_acc: 0.7653
Epoch 41/50
390/390 [==============================] - 28s 73ms/step - loss: 0.3106 - acc: 0.8883 - val_loss: 0.8601 - val_acc: 0.7497
Epoch 42/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3073 - acc: 0.8896 - val_loss: 0.8276 - val_acc: 0.7640
Epoch 43/50
390/390 [==============================] - 29s 73ms/step - loss: 0.3003 - acc: 0.8912 - val_loss: 0.8111 - val_acc: 0.7607
Epoch 44/50
390/390 [==============================] - 28s 73ms/step - loss: 0.3025 - acc: 0.8914 - val_loss: 0.9401 - val_acc: 0.7403
Epoch 45/50
390/390 [==============================] - 28s 73ms/step - loss: 0.2931 - acc: 0.8937 - val_loss: 0.8615 - val_acc: 0.7536
Epoch 46/50
390/390 [==============================] - 29s 73ms/step - loss: 0.2939 - acc: 0.8924 - val_loss: 0.8037 - val_acc: 0.7669
Epoch 47/50
390/390 [==============================] - 28s 73ms/step - loss: 0.2892 - acc: 0.8962 - val_loss: 0.8202 - val_acc: 0.7599
Epoch 48/50
390/390 [==============================] - 29s 74ms/step - loss: 0.2807 - acc: 0.8980 - val_loss: 0.9023 - val_acc: 0.7501
Epoch 49/50
390/390 [==============================] - 28s 73ms/step - loss: 0.2866 - acc: 0.8974 - val_loss: 0.8428 - val_acc: 0.7599
Epoch 50/50
390/390 [==============================] - 29s 74ms/step - loss: 0.2716 - acc: 0.9014 - val_loss: 0.7970 - val_acc: 0.7710
Model took 1447.87 seconds to train

Accuracy on test data is: 77.10


