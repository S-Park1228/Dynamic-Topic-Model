# capturing_issues_with_DTM_and_BIGKINDS
It was written to capture issues in Korean news data through Dynamic Topic Model. The news data source is BIGKINDS, which is one of the biggest news data archives in Korea.

# Data Source: BIGKINDS
- URL: https://www.bigkinds.or.kr/
- Data: reporter's name, news date, publishing companies, categories, news title, the body of news articles(split by spacing)
- You need news date, news title and the body of news articles to use the Topic Model.

# Remarks
- It is desirable for users to collect news data by a certain news category to make fully use of this model.
- For practical use, collect the number of news data no more than 10,000.
- It uses konlpy(mecab) for NLP. So if you need to add some names regarding a person, a region and so on, use its(mecab) instructions.
- stopwords-ko.txt attached
