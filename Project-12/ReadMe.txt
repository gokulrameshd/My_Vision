
David Page:

-Try to run on single GPU
-Art of the state 345s/1 GPU and 174s/8 GPUs

Post-1 :Baseline
-Remove bottlenecks
-Mixed Precision computation
-Smaller networks with capacity and Higher learning rates.
-18 layer RESNET
-SGD optimizer
-34 Epochs
-V100 GPU 
-Batch normalization -> ReLU
-Image Processing :Padding,normalization,transposition,random cropping and flipping
-training time reduced to 297s

Post-2 :Mini-Batches
-batch_size : increased from 128 to 512
-gradients are summed, not averaged.
-training time reduced to 256s

Post-3 :Regularisation
-CutOut : zeroing out a random subset,8×8 square subsets of the training images
-batch size:768 ,momentum = 0.9,weight decay = 5e-4
-mix up regularisation
-Training time reduced to 154s

Post-4 :Architecture 
-Instead of 1X1 use 3X3 conv + pooling
-Global Average pooling before classifier
-L1+L2+L3

Post-5 :Hyperparameters
- w?(1–?a)w
- Weight decay in the presence of batch normalisation acts as a 
  stable control mechanism on the effective step size.

Post-6 :Weight decay

Post-7 :Batch Normalization
-Helps in optimization like internal covariate shift.
-Batch norm enables high learning rate.

Post-8 :Bag of tricks
-9 layer ResNet
-TTA
-unit8 format
-data augmentation on GPU
-model converted to float16.
-conv->pool->norm->activation
-Label smoothing
-CELU activation function
-Ghost batch norm :512 
-Frozen Batch Norm scales 
-Input patch whitening :Global PCA(ZCA)
-cut out reduced from 8x8 to 5x5
-Exponential Moving Averages:update every 5 batches
-Test-Time Augmentation

#####################################################################

David Yang:

-Davidnet  - 9 layer resnet
-TPU
-BATCH_SIZE = 512 
-MOMENTUM = 0.9 
-WEIGHT_DECAY = 0.000125 
-LEARNING_RATE = 0.4 
-EPOCHS = 24 
-WARMUP = 5 
-TFrecords,using Protobuf serialization library
-padded to 40x40
-cropped to 32x32
-cutout ,random flipping
-SGD ,Nestrov momentum
-Slanted triangular learning rate scheduler


