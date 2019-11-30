# Accuracy of base network: 82.28

Epoch 42/50
390/390 [==============================] - 7s 17ms/step - loss: 0.3279 - acc: 0.8916 - val_loss: 0.5902 - val_acc: 0.8262
Epoch 43/50
390/390 [==============================] - 7s 17ms/step - loss: 0.3304 - acc: 0.8890 - val_loss: 0.5752 - val_acc: 0.8264
Epoch 44/50
390/390 [==============================] - 7s 17ms/step - loss: 0.3219 - acc: 0.8908 - val_loss: 0.5842 - val_acc: 0.8282
Epoch 45/50
390/390 [==============================] - 7s 17ms/step - loss: 0.3190 - acc: 0.8936 - val_loss: 0.5865 - val_acc: 0.8218
Epoch 46/50
390/390 [==============================] - 7s 17ms/step - loss: 0.3173 - acc: 0.8935 - val_loss: 0.6229 - val_acc: 0.8173
Epoch 47/50
390/390 [==============================] - 7s 17ms/step - loss: 0.3116 - acc: 0.8945 - val_loss: 0.6012 - val_acc: 0.8214
Epoch 48/50
390/390 [==============================] - 7s 17ms/step - loss: 0.3104 - acc: 0.8974 - val_loss: 0.5823 - val_acc: 0.8208
Epoch 49/50
390/390 [==============================] - 7s 17ms/step - loss: 0.3132 - acc: 0.8963 - val_loss: 0.5925 - val_acc: 0.8217
Epoch 50/50
390/390 [==============================] - 7s 17ms/step - loss: 0.3040 - acc: 0.8999 - val_loss: 0.6163 - val_acc: 0.8228


# Model defintion:
model2.add(SeparableConv2D(64, 3, 3, activation='relu', border_mode='same', input_shape=(32,32,3))) # out: 32*32*64  , RF: 3
model2.add(Activation('relu'))
model2.add(SeparableConv2D(64, 3, 3)) # out: 30*30*64, RF:5
model2.add(Activation('relu'))
model2.add(MaxPooling2D(pool_size=(2,2))) # out: 15*15*64, RF 6
model2.add(Dropout(0.1))
model2.add(BatchNormalization())

model2.add(SeparableConv2D(114, 3, 3, border_mode='same')) # out: 15*15*114, RF: 10
model2.add(Activation('relu'))
model2.add(SeparableConv2D(114, 3, 3)) # out: 13*13*114, RF: 14
model2.add(Activation('relu'))
model2.add(MaxPooling2D(pool_size=(2,2))) # out: 6*6*114, RF: 16
model2.add(Dropout(.1))
model2.add(BatchNormalization())

model2.add(SeparableConv2D(192, 3, 3, border_mode='same')) # out: 6*6*192, RF : 24
model2.add(Activation('relu'))
model2.add(SeparableConv2D(192, 3, 3)) # out: 4*4*192, RF: 32
model2.add(Activation('relu'))
model2.add(MaxPooling2D(pool_size=(2,2))) # out: 2*2*192, 36

model2.add(Flatten())

model2.add(Dense(num_classes, activation='softmax'))
model2.compile(optimizer=Adam(lr=.003), loss='categorical_crossentropy', metrics=['accuracy'])

# 50 epoch logs:

### Max test accuracy: 80.86

Epoch 1/50
390/390 [==============================] - 34s 88ms/step - loss: 1.6672 - acc: 0.3872 - val_loss: 1.4314 - val_acc: 0.4876
Epoch 2/50
390/390 [==============================] - 29s 75ms/step - loss: 1.2873 - acc: 0.5414 - val_loss: 1.1742 - val_acc: 0.5891
Epoch 3/50
390/390 [==============================] - 29s 75ms/step - loss: 1.1455 - acc: 0.5932 - val_loss: 1.1056 - val_acc: 0.6150
Epoch 4/50
390/390 [==============================] - 30s 76ms/step - loss: 1.0536 - acc: 0.6271 - val_loss: 1.1187 - val_acc: 0.6129
Epoch 5/50
390/390 [==============================] - 29s 74ms/step - loss: 0.9811 - acc: 0.6533 - val_loss: 0.9075 - val_acc: 0.6801
Epoch 6/50
390/390 [==============================] - 29s 74ms/step - loss: 0.9255 - acc: 0.6778 - val_loss: 1.1530 - val_acc: 0.6337
Epoch 7/50
390/390 [==============================] - 29s 74ms/step - loss: 0.8786 - acc: 0.6923 - val_loss: 0.9112 - val_acc: 0.6855
Epoch 8/50
390/390 [==============================] - 29s 74ms/step - loss: 0.8431 - acc: 0.7045 - val_loss: 0.8629 - val_acc: 0.7057
Epoch 9/50
390/390 [==============================] - 29s 74ms/step - loss: 0.8126 - acc: 0.7155 - val_loss: 1.0333 - val_acc: 0.6558
Epoch 10/50
390/390 [==============================] - 29s 73ms/step - loss: 0.7929 - acc: 0.7240 - val_loss: 0.7472 - val_acc: 0.7461
Epoch 11/50
390/390 [==============================] - 29s 74ms/step - loss: 0.7680 - acc: 0.7325 - val_loss: 0.7410 - val_acc: 0.7444
Epoch 12/50
390/390 [==============================] - 28s 73ms/step - loss: 0.7428 - acc: 0.7408 - val_loss: 0.8527 - val_acc: 0.7185
Epoch 13/50
390/390 [==============================] - 29s 74ms/step - loss: 0.7244 - acc: 0.7456 - val_loss: 0.7560 - val_acc: 0.7435
Epoch 14/50
390/390 [==============================] - 29s 73ms/step - loss: 0.7157 - acc: 0.7490 - val_loss: 0.7687 - val_acc: 0.7438
Epoch 15/50
390/390 [==============================] - 29s 73ms/step - loss: 0.7005 - acc: 0.7551 - val_loss: 0.7795 - val_acc: 0.7310
Epoch 16/50
390/390 [==============================] - 29s 74ms/step - loss: 0.6836 - acc: 0.7602 - val_loss: 0.8330 - val_acc: 0.7278
Epoch 17/50
390/390 [==============================] - 29s 73ms/step - loss: 0.6778 - acc: 0.7632 - val_loss: 0.7576 - val_acc: 0.7492
Epoch 18/50
390/390 [==============================] - 29s 74ms/step - loss: 0.6658 - acc: 0.7682 - val_loss: 0.6944 - val_acc: 0.7749
Epoch 19/50
390/390 [==============================] - 29s 73ms/step - loss: 0.6513 - acc: 0.7718 - val_loss: 0.7003 - val_acc: 0.7666
Epoch 20/50
390/390 [==============================] - 29s 73ms/step - loss: 0.6451 - acc: 0.7745 - val_loss: 0.8030 - val_acc: 0.7385
Epoch 21/50
390/390 [==============================] - 29s 74ms/step - loss: 0.6328 - acc: 0.7812 - val_loss: 0.7569 - val_acc: 0.7519
Epoch 22/50
390/390 [==============================] - 28s 73ms/step - loss: 0.6335 - acc: 0.7784 - val_loss: 0.6145 - val_acc: 0.7931
Epoch 23/50
390/390 [==============================] - 29s 73ms/step - loss: 0.6138 - acc: 0.7833 - val_loss: 0.6756 - val_acc: 0.7821
Epoch 24/50
390/390 [==============================] - 29s 74ms/step - loss: 0.6112 - acc: 0.7841 - val_loss: 0.6855 - val_acc: 0.7710
Epoch 25/50
390/390 [==============================] - 29s 75ms/step - loss: 0.6025 - acc: 0.7890 - val_loss: 0.7123 - val_acc: 0.7708
Epoch 26/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5928 - acc: 0.7934 - val_loss: 0.6880 - val_acc: 0.7741
Epoch 27/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5916 - acc: 0.7922 - val_loss: 0.6879 - val_acc: 0.7819
Epoch 28/50
390/390 [==============================] - 28s 73ms/step - loss: 0.5841 - acc: 0.7955 - val_loss: 0.6886 - val_acc: 0.7733
Epoch 29/50
390/390 [==============================] - 29s 73ms/step - loss: 0.5793 - acc: 0.7980 - val_loss: 0.7680 - val_acc: 0.7529
Epoch 30/50
390/390 [==============================] - 28s 72ms/step - loss: 0.5756 - acc: 0.7986 - val_loss: 0.6987 - val_acc: 0.7750
Epoch 31/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5653 - acc: 0.8020 - val_loss: 0.6969 - val_acc: 0.7774
Epoch 32/50
390/390 [==============================] - 29s 73ms/step - loss: 0.5591 - acc: 0.8039 - val_loss: 0.5776 - val_acc: 0.8071
Epoch 33/50
390/390 [==============================] - 28s 73ms/step - loss: 0.5553 - acc: 0.8060 - val_loss: 0.6955 - val_acc: 0.7735
Epoch 34/50
390/390 [==============================] - 28s 72ms/step - loss: 0.5477 - acc: 0.8069 - val_loss: 0.6512 - val_acc: 0.7894
Epoch 35/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5498 - acc: 0.8092 - val_loss: 0.6342 - val_acc: 0.8007
Epoch 36/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5415 - acc: 0.8079 - val_loss: 0.6384 - val_acc: 0.7924
Epoch 37/50
390/390 [==============================] - 29s 73ms/step - loss: 0.5409 - acc: 0.8104 - val_loss: 0.5889 - val_acc: 0.8069
Epoch 38/50
390/390 [==============================] - 29s 73ms/step - loss: 0.5347 - acc: 0.8128 - val_loss: 0.6379 - val_acc: 0.7955
Epoch 39/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5335 - acc: 0.8129 - val_loss: 0.6345 - val_acc: 0.7978
Epoch 40/50
390/390 [==============================] - 29s 73ms/step - loss: 0.5297 - acc: 0.8133 - val_loss: 0.7550 - val_acc: 0.7641
Epoch 41/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5238 - acc: 0.8162 - val_loss: 0.6788 - val_acc: 0.7871
Epoch 42/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5237 - acc: 0.8169 - val_loss: 0.6906 - val_acc: 0.7819
Epoch 43/50
390/390 [==============================] - 29s 73ms/step - loss: 0.5238 - acc: 0.8150 - val_loss: 0.6598 - val_acc: 0.7898
Epoch 44/50
390/390 [==============================] - 29s 73ms/step - loss: 0.5193 - acc: 0.8165 - val_loss: 0.6583 - val_acc: 0.7888
Epoch 45/50
390/390 [==============================] - 28s 73ms/step - loss: 0.5133 - acc: 0.8188 - val_loss: 0.6819 - val_acc: 0.7844
Epoch 46/50
390/390 [==============================] - 29s 73ms/step - loss: 0.5021 - acc: 0.8230 - val_loss: 0.6304 - val_acc: 0.7990
Epoch 47/50
390/390 [==============================] - 29s 74ms/step - loss: 0.5095 - acc: 0.8196 - val_loss: 0.6210 - val_acc: 0.7934
Epoch 48/50
390/390 [==============================] - 29s 73ms/step - loss: 0.4943 - acc: 0.8266 - val_loss: 0.6168 - val_acc: 0.8086
Epoch 49/50
390/390 [==============================] - 28s 72ms/step - loss: 0.5042 - acc: 0.8243 - val_loss: 0.5962 - val_acc: 0.8062
Epoch 50/50
390/390 [==============================] - 28s 73ms/step - loss: 0.4991 - acc: 0.8226 - val_loss: 0.7044 - val_acc: 0.7830
Model 2 took 1439.60 seconds to train
