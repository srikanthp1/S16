# transformer encoder-decoder training - TRANSLATIOn

## About

* goal is to train an encoder decoder architecture for language translation
* dataset is en-fr from opus transformers 
* everything over 150 words and +10 translation words sentences are removed 
* should also work on removing small sentences and integrating uniform length batch training 

## training 

* we are using 8 heads and 6 repeat encoders with 'parameter sharing'
* we fixed input length to 150 and output can be upto 160 because of +10 buffer
* we are using padding upto 150 token and training can be done faster if we used dynamic padding which we will do.
* we also used amp precision to get benefit of training some layers with 16-precision and some with 32-precision based on accuracy performance.
* didnt change relu as we are not training for longer
* changed squeeze expand layer to 256 as it can save us some time in training
* pending is to start taking inspiration from fastvit of apple to get faster inference.

## results

* because of above implementations i was able to achieve 1.5 loss but still there is room to improve by training longer
* last 3 epochs saw a good performance than the 7 epochs before that 
