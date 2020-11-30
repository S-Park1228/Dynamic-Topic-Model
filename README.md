# capturing_issues_with_DTM_and_BIGKINDS
It was written to capture issues in Korean news data through Dynamic Topic Model. The news data source is BIGKINDS, which is one of the biggest news data archives in Korea.

# Data Source: BIGKINDS
- URL: https://www.bigkinds.or.kr/
- Data: reporter's name, news date, publishing companies, categories, news title, the body of news articles(split by spacing)
- You need news date, news title and the body of news articles to use the Topic Model.

# Sample
- I used the news regarding the BIKINDS trade category to test whether the model could have succeeded in capturing U.S>-China trade dispute in March 2018.
- Period: Sep. 2017 ~ Mar. 2018
- Data: Trade category news from the major Korean publishing companies.
- The number of obs: 8215

# Remarks
- It is desirable for users to collect news data by a certain news category to make fully use of this model.
- For practical use, collect the number of news data no more than 10,000.
- It uses konlpy(mecab) for NLP. So if you need to add some names regarding a person, a region and so on, use its(mecab) instructions.
- stopwords-ko.txt attached
- I used Jupyter Notebook conda_python3
- AWS Lifecycle configurations: I used Amazon web services to implement this project. So please refer to AWS Lifecycle configurations as follows.

# AWS Lifecycle configurations
#!/bin/bash

set -e

< install Korean font >
sudo mkdir -p /usr/share/fonts/truetype/malgun
sudo cp /home/ec2-user/SageMaker/malgun.ttf /usr/share/fonts/truetype/malgun/

< Install mecab-ko >
wget https://bitbucket.org/eunjeon/mecab-ko/downloads/mecab-0.996-ko-0.9.1.tar.gz
tar zxfv mecab-0.996-ko-0.9.1.tar.gz
cd mecab-0.996-ko-0.9.1
./configure
make
make check
sudo make install

< Install mecab-ko-dic >
wget https://bitbucket.org/eunjeon/mecab-ko-dic/downloads/mecab-ko-dic-1.6.1-20140814.tar.gz
tar zxfv mecab-ko-dic-1.6.1-20140814.tar.gz
cd mecab-ko-dic-1.6.1-20140814
autoreconf -f -i
./configure
sudo ldconfig
make
sudo sh -c 'echo "dicdir=/usr/local/lib/mecab/dic/mecab-ko-dic" > /usr/local/etc/mecabrc'
sudo make install

< Install Chrome >
wget https://chromedriver.storage.googleapis.com/2.37/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
mv chromedriver /usr/bin/chromedriver
nohup curl https://intoli.com/install-google-chrome.sh | bash &
