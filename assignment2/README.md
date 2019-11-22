# Epoch results
Train on 60000 samples, validate on 10000 samples
Epoch 1/20

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
60000/60000 [==============================] - 15s 246us/step - loss: 0.1265 - acc: 0.9451 - val_loss: 0.0342 - val_acc: 0.9901
Epoch 2/20

Epoch 00002: LearningRateScheduler setting learning rate to 0.002269289.
60000/60000 [==============================] - 8s 135us/step - loss: 0.1156 - acc: 0.9482 - val_loss: 0.0215 - val_acc: 0.9935
Epoch 3/20

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018248175.
60000/60000 [==============================] - 8s 135us/step - loss: 0.1102 - acc: 0.9501 - val_loss: 0.0278 - val_acc: 0.9915
Epoch 4/20

Epoch 00004: LearningRateScheduler setting learning rate to 0.001525941.
60000/60000 [==============================] - 8s 136us/step - loss: 0.1094 - acc: 0.9487 - val_loss: 0.0182 - val_acc: 0.9940
Epoch 5/20

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013111888.
60000/60000 [==============================] - 8s 136us/step - loss: 0.1020 - acc: 0.9516 - val_loss: 0.0185 - val_acc: 0.9937
Epoch 6/20

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011494253.
60000/60000 [==============================] - 8s 134us/step - loss: 0.0997 - acc: 0.9528 - val_loss: 0.0200 - val_acc: 0.9936
Epoch 7/20

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010231924.
60000/60000 [==============================] - 8s 135us/step - loss: 0.1008 - acc: 0.9506 - val_loss: 0.0190 - val_acc: 0.9942
Epoch 8/20

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009219422.
60000/60000 [==============================] - 8s 136us/step - loss: 0.0992 - acc: 0.9520 - val_loss: 0.0188 - val_acc: 0.9945
Epoch 9/20

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008389262.
60000/60000 [==============================] - 8s 135us/step - loss: 0.0954 - acc: 0.9531 - val_loss: 0.0156 - val_acc: 0.9953
Epoch 10/20

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007696254.
60000/60000 [==============================] - 8s 134us/step - loss: 0.0974 - acc: 0.9505 - val_loss: 0.0170 - val_acc: 0.9947
Epoch 11/20

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007109005.
60000/60000 [==============================] - 8s 136us/step - loss: 0.0951 - acc: 0.9526 - val_loss: 0.0223 - val_acc: 0.9936
Epoch 12/20

Epoch 00012: LearningRateScheduler setting learning rate to 0.000660502.
60000/60000 [==============================] - 8s 136us/step - loss: 0.0954 - acc: 0.9533 - val_loss: 0.0184 - val_acc: 0.9949
Epoch 13/20

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006167763.
60000/60000 [==============================] - 8s 134us/step - loss: 0.0946 - acc: 0.9535 - val_loss: 0.0177 - val_acc: 0.9949
Epoch 14/20

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005784805.
60000/60000 [==============================] - 8s 135us/step - loss: 0.0936 - acc: 0.9520 - val_loss: 0.0168 - val_acc: 0.9952
Epoch 15/20

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005446623.
60000/60000 [==============================] - 8s 137us/step - loss: 0.0937 - acc: 0.9530 - val_loss: 0.0181 - val_acc: 0.9945
Epoch 16/20

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005145798.
60000/60000 [==============================] - 8s 138us/step - loss: 0.0915 - acc: 0.9536 - val_loss: 0.0172 - val_acc: 0.9954
Epoch 17/20

Epoch 00017: LearningRateScheduler setting learning rate to 0.0004876463.
60000/60000 [==============================] - 8s 135us/step - loss: 0.0923 - acc: 0.9531 - val_loss: 0.0171 - val_acc: 0.9949
Epoch 18/20

Epoch 00018: LearningRateScheduler setting learning rate to 0.000463392.
60000/60000 [==============================] - 8s 137us/step - loss: 0.0919 - acc: 0.9526 - val_loss: 0.0170 - val_acc: 0.9953
Epoch 19/20

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004414361.
60000/60000 [==============================] - 8s 136us/step - loss: 0.0912 - acc: 0.9529 - val_loss: 0.0173 - val_acc: 0.9948
Epoch 20/20

Epoch 00020: LearningRateScheduler setting learning rate to 0.0004214667.
60000/60000 [==============================] - 8s 136us/step - loss: 0.0909 - acc: 0.9533 - val_loss: 0.0164 - val_acc: 0.9952

# Model evaluation result
[0.01644214096760843, 0.9952]

# Strategy
Results could be achieved without major additions to the previous (eigth) model. There were unnecessary kernels later in the process which I reduced from 16 to 15. This lead to a reduction of total params to 15070. Also I introduced use_bias=False for all convolutional layers.

In the initial runs I saw some overfitting because of which validation accuracy wasn't increasing in proportion to training accuracy until epoch 14/15 so I increased the dropouts marginally to .11 . This stabalized the results after epoch 11.

I also tweaked the learning rate to (0.003 * 1/(1 + 0.322 * epoch) from the previous (0.003 * 1/(1 + 0.319 * epoch). This lead to marginally better convergence rate although as can be seen in the current run training accuracy still fluctuates throughout 20 epochs so we might require more aggressive fine-tuning.

