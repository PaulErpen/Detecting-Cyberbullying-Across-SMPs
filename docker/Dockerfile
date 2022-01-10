FROM python:2.7.18-buster
COPY ../ ./Cyberbullying
RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
RUN python get-pip.py
RUN pip install matplotlib==2.2.3
RUN pip install numpy==1.16.6
RUN pip install keras==2.0.6
RUN pip install pandas==0.24.2
RUN pip install scipy==1.2.3
RUN pip install decorator==4.4.2
RUN pip install ipywidgets==7.5
RUN pip install tweet-preprocessor==0.4.0
RUN pip install tensorflow==1.15.0
RUN pip install tflearn==0.5.0
RUN pip install argparse==1.4.0
RUN pip install scikit-learn==0.19.0
RUN pip install textblob==0.17.1
RUN pip install jupyter[notebook]==1.0.0
EXPOSE 8796
CMD jupyter notebook --ip=127.0.0.1 --port=8796 --allow-root