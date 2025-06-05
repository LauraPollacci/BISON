# BISON

This repository describes the **BISON** framework (*Blockchain Interpretable Success prediction for SOcial media NFTs*), which leverages linguistic statistics and blockchain-derived features to model and explain the success of blockchain-native articles (e.g., writing NFTs).

---

# Feature Description 
Below are the features used in the model, categorized by type. These features are used in a "multimodal", explainable ML pipeline to predict and interpret success on decentralized content platforms.

## Readability Indices & Linguistic Statistics

These features are extracted from the textual content of articles:

### Readability Metrics (3)

- `Kincaid Grade Level`: U.S. grade level required to understand the text.  
- `Flesch Reading Ease`: Score from 0–100; higher means easier.  
- `Gunning Fog Index`: Years of formal education required.  

### Statistical Linguistic Features (13)

- `characters_per_word`: Average characters per word  
- `syll_per_word`: Average syllables per word  
- `words_per_sentence`: Average words per sentence  
- `sentences_per_paragraph`: Average sentences per paragraph  
- `type_token_ratio`: Lexical diversity (% of unique word types over total tokens)  
- `characters`: Total character count  
- `syllables`: Total syllable count  
- `words`: Number of content tokens  
- `wordtypes`: Number of unique content word types  
- `sentences`: Total sentence count  
- `paragraphs`: Total paragraph count  
- `long_words`: Words with more than 6 letters  
- `complex_words`: Polysyllabic and uncommon words  

### Advanced Linguistic & NLP Features (16)

- `cleaned_text`: Text after removing noise and irrelevant characters  
- `language`: Detected language of the text  
- `cleaned_body`: Cleaned version of the article body text  
- `cleaned_title`: Cleaned article title  
- `processed_cleaned_text`: Text after further processing like normalization  
- `cleaned_text_tokenized`: Tokenized version of the cleaned text  
- `cleaned_text_lemmatized`: Lemmatized tokens (base forms of words)  
- `cleaned_text_POS`: Part-of-speech tagging of tokens  
- `cleaned_text_sentiment`: Sentiment score derived from text  
- `words_body`: Word count in the article body  
- `words_title`: Word count in the title  
- `words_text`: Total word count combining title and body  
- `normalized_tfidf_sum`: Normalized sum of TF-IDF scores across document  
- `verbs_density`: Density of verbs in text  
- `adjectives_density`: Density of adjectives in text  
- `nouns_density`: Density of nouns in text

---

## Topic-Related (8)

Thematic topics extracted from articles:

- `topic`: (categorical)  Represents the main topic of the article. Possible values are: T1: Gaming, Virtual Worlds & Characters; T2: Wallets, Airdrops & Ethereum Tools; T3: Web3, Blockchain & Digital Platforms; T4: DeFi, Market Strategies & Liquidity; T5: Blockchain, Transactions & Smart Contracts; T6: Web3 Launches, Rewards & Creators; T7: Human Thoughts, Emotions & Reflections.
- `topic_T1: Gaming, Virtual Worlds & Characters`  
- `topic_T2: Wallets, Airdrops & Ethereum Tools`  
- `topic_T3: Web3, Blockchain & Digital Platforms`  
- `topic_T4: DeFi, Market Strategies & Liquidity`  
- `topic_T5: Blockchain, Transactions & Smart Contracts`  
- `topic_T6: Web3 Launches, Rewards & Creators`  
- `topic_T7: Human Thoughts, Emotions & Reflections`

---

## Keyword-Based (7)
For each keyword (`nft`, `web3`, `community`, `blockchain`, `crypto`, `wallet`, `chain`):

- `<keyword>`: indicates the presence (1) or absence (0) of the keyword in the article text.

---

### Temporal (7)

- `days_since_epoch`: Days elapsed since article publication
- `publication_date`: Full publication date of the article or NFT in `YYYY-MM-DD` format.
- `year_month`: Publication date grouped by year and month in `YYYY-MM` format, useful for temporal aggregation.
- `year`: Year of publication  
- `month`: Month of publication (values from 1 to 12)  
- `day`: Day of publication  
- `weekday`: Weekday of publication, encoded as 0=Monday, 1=Tuesday, 2=Wednesday, 3=Thursday, 4=Friday, 5=Saturday, 6=Sunday


---

## Blockchain-Related Features

These features capture blockchain and crypto ecosystem signals relevant to each article:


### Market Indicators (6*6=36)

For each token (`BTC`, `TETHER`, `OPTIMISM`, `ETH`, `USDC`, `DAI`) at the publication date:

- `open_<token>_usd`: Opening price  
- `last_<token>_usd`: Closing price  
- `max_<token>_usd`: Daily maximum  
- `min_<token>_usd`: Daily minimum  
- `vol_<token>`: Trading volume  
- `var%_<token>`: Daily % price change  

### Blockchain Activity (5)

- `daily_transactions_optimism`: Daily transaction count on Optimism network  
- `eth_active_addresses_total`: Total active Ethereum addresses  
- `eth_active_addresses_sender`: Active sending addresses on Ethereum  
- `eth_active_addresses_receiver`: Active receiving addresses on Ethereum  
- `optimism_active_addresses_total`: Total active addresses on Optimism network

---

## Author Wallet Features and Platform Activity (7)

- `author_address`: Wallet address of the author  
- `author_ether_balance`: ETH balance of author's wallet  
- `author_transactions_number`: Total blockchain transactions by author
- `authorPostCount`: Number of published articles by author  
- `authorTotalSales`: Number of Writing NFTs sold by author  
- `authorTotalRevenue`: Total ETH revenue from NFT sales by author
- `Author Homepage`: URL of the author's homepage or profile  

---

## NFT and Article Metadata (15)

- `writing_nft`: Identifier indicating the article is minted as a writing NFT  
- `Total Sold(ETH)`: Total ETH earned from all sales of the NFT  
- `Total Sold Numbers`: Total quantity of NFTs sold  
- `Total Buyers`: Number of unique buyers  
- `Price(ETH)`: Listing or sale price of the NFT  
- `nft_address`: Blockchain address of the NFT contract  
- `collection`: Name of the NFT collection  
- `fees`: Associated fees (e.g., royalties) on NFT sales  
- `created_date`: Date of NFT or article creation  
- `link`: URL to the article or NFT page  
- `digest`: Unique content hash or digest  
- `transaction_id`: Blockchain transaction ID for mint or sale  
- `body`: Raw text body of the article  
- `timestamp`: Timestamp of article or NFT event  
- `title`: Raw article title  

---

## Success Metrics (2)

- `Success`: Numeric indicator of article success  
- `SuccessBinary`: Binary success label (success/failure)

---

## Google Trends-Related (5)

- `week_google_searches_nft`: Google Trends score for "nft" in publication week  
- `week_google_searches_crypto`: Google Trends score for "crypto"  
- `week_google_searches_bitcoin`: Google Trends score for "bitcoin"  
- `week_google_searches_ethereum`: Google Trends score for "ethereum"  
- `week_google_searches_optimism`: Google Trends score for "optimism"
