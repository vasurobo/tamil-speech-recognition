# Tamil Speech Recognizer
# (CMU Sphinx-4 / Pocketsphinx)
Tamil Speech Recognizer (OFFLINE) - Acoustic (am) & Language Models (lm) for tamil language

# Requirements
* Pocketsphinx should be installed
# Supports
* Supports both Linux and Windows (also RaspberryPi Zero/W/1/2/3/4)

# Installation Instructions

Firstly, we should install pocketsphinx (can also work on Sphinx 4)

# On Ubuntu

Run the below code on terminal to install all the dependencies.

sudo apt-get install gcc automake autoconf libtool bison swig python-dev libpulse-dev

Then, lets install sphinxbase (Important for running pocketsphinx)

git clone https://github.com/cmusphinx/sphinxbase.git  
cd sphinxbase  
./autogen.sh  
make  
sudo make install  


Now, install pocketsphinx  

git clone https://github.com/cmusphinx/pocketsphinx.git  
cd pocketsphinx  
./autogen.sh   
make  
sudo make install  

Next open ld.so.conf file  

sudo nano /etc/ld.so.conf  
# Note : add the /usr/local/lib directory at the end of file, then run the below command  
sudo ldconfig  

# Check wether pocketsphinx is installed correctly : Run.

pocketsphinx_continuous  

Thats all.  

Now download Tamil Speech Recognizer from https://github.com/vasurobo/tamil-speech-recognition/ and run "./run.sh" file in terminal.  


Check and configure your microphone volume for better accuracy, then speak on microphone.

# Example :

நன்றி  
அப்துல் கலாம்  
வணக்கம்  
உன் பெயர் என்ன 

# The words may appear weird because terminal can't display tamil correctly.

So, you can redirect the recognized words alone to a text file and check it wether it recognize the words you speak correctly. Run the below code redirect output to text files.

pocketsphinx_continuous -hmm am/ta.cd_cont_3000 -lm lm/ta.lm.bin -dict lm/ta.dic -inmic yes 2>./unwanted-stuff.log | tee ./words.log

Open "words.log" file to see the recognized words.

Currently WER 28%

# TODO
* Build Tamil ASR system on Kaldi
* Achieve atleast 19% WER
* Setup Speech Server
* Integrate with Tamil Speech Synthesizer (IIT Donlab)
* Integrate with Tamil Intent Parser (like Rasa stack)
* Build a full fledged custom Tamil Assistant

@jarvisvasu
@vasurobo

Check out : https://vasurobo.com


