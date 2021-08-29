# Using Deep Learning To Support Logging Activities

In thiw work we present LANCE(Log stAtemeNt reCommEnder), a fully-fledge deep learning approach for supporting the task of log statemtent injection in the context of Java.
LANCE, is built on the recently proposed Text-To-Text Transfer Transformer (T5) architecture (https://github.com/google-research/text-to-text-transfer-transformer), which has been proved to reach SOTA results when supporting <a href="">code-related tasks</a>


#### How to experiment with LANCE

Before training the [T5 small](https://github.com/google-research/text-to-text-transfer-transformer), namely the core of LANCE, it is important to also train a new tokenizer (sentencepiece model) to accomodate the expanded vocabulary given by the java programming language. For such, we used the raw pre-training instances(Java corpus) + English sentences from the well known C4 dataset


*  ##### How to train a new <a href='https://github.com/google/sentencepiece/blob/master/python/README.md'>SentencePiece Model</a>

    *Pythonic way*

    ```
    pip install sentencepiece==0.1.96
    import sentencepiece as spm
    spm.SentencePieceTrainer.train('--input=all_sp.txt --model_prefix=LOG_SP --vocab_size=32000 --bos_id=-1  --eos_id=1 --unk_id=2 --pad_id=0 --shuffle_input_sentence=true --character_coverage=1.0 --user_defined_symbols=“<LOG_STMT>”') 
    ```

    Under this path we also provide our trained tokenizer: https://github.com/lance-log/lance/tree/main/Code

* ##### Set up a GCS Bucket
    To Set up a new GCS Bucket for training and fine-tuning a T5 Model, please follow the orignal guide provided by <a href='https://www.google.com'> Google </a> Here the link: https://cloud.google.com/storage/docs/quickstart-console


* ##### Datasets

    The datasets for pre-training, fine-tuning, validating and finally testing LANCE can be found at this link: https://drive.google.com/drive/folders/1D12y-CIJTYLxMeSmGQjxEXjTEzQImgaH?usp=sharing

* ##### Pre-trainig/Fine-tuning 
  
    To pre-train and then, fine-tune LANCE, please use the following:
    - <a href ='https://github.com/lance-log/lance/blob/main/Code/Pre-training/Pre_training.ipynb'>Pre-Training</a> 
    -  <a href ='https://github.com/lance-log/lance/blob/main/Code/Fine-tuning/Fine_Tuning.ipynb'>Fine-Tuning</a> 



* ##### Models
  * <a href="https://drive.google.com/drive/folders/1vqNozabCLoAgIG8qJJ6qs0W8s77-FrPc?usp=sharing">Pre-trained on the tasks mixture (Multi-Task)</a>
  * <a href="https://drive.google.com/drive/folders/15Wx9dBlqQxV1zFeHl_uh2JoRBZ9oPt4l?usp=sharing">Pre-trained on LogSTMT only Task</a>
  * <a href="https://drive.google.com/drive/folders/1CU_rS-BX9BchUhQEbis4CYH2w6syJ6i2?usp=sharing">Pre-trained on Denoise only Task</a>
  * <a href="https://drive.google.com/drive/folders/1SjIdfQUDPH5NI5KseHypkln0yiYN8-Jr?usp=sharing">No Pre-trained</a>
  
* ##### Results:  :open_file_folder: 
    * <a href='https://drive.google.com/drive/folders/1Kutaau3q5vPP3phaWtdmouZ5bvHHipwM?usp=sharing'>Multi-Task</a>
    * <a href="https://drive.google.com/drive/folders/1cPJElLO_C1MoPp0dWAlmPX77CMNW0SAP?usp=sharing">LogSTMT only Task</a>
    * <a href="https://drive.google.com/drive/folders/1Ea4WxrdxD4nPOeOLsoSonM7NYqKe-Snn?usp=sharing">Denoising only Task</a>
    * <a href="https://drive.google.com/drive/folders/1FRERpcgcEdG6b7Cp4WpURbZR3TGtGa6I?usp=sharing">No Pre-trained</a>


* ##### Additional:
    Under <a href='https://github.com/code-comment/anon/tree/main/Miscellaneous'>Miscellaneous</a>, you can find all the additional materials we used for computing the results (i.e; the Java program which relies on GumTree)





    

