# BISON

This repository describes the **BISON** framework (*Blockchain Interpretable Success prediction for SOcial media NFTs*), which leverages linguistic statistics and blockchain-derived features to model and explain the success of blockchain-native articles (e.g., writing NFTs).

---

# Feature Description 
Below are the features used in the model, categorized by type. These features are used in a "multimodal", explainable ML pipeline to predict and interpret success on decentralized content platforms.

## Readability Indices & Linguistic Statistics

These features are extracted from the textual content of articles:

### Readability Metrics

- **`Kincaid Grade Level`**: U.S. grade level required to understand the text.  
- **`Automated Readability Index (ARI)`**: Based on characters and sentence length.  
- **`Coleman-Liau Index`**: Grade level based on character counts.  
- **`Flesch Reading Ease`**: Score from 0–100; higher means easier.  
- **`Gunning Fog Index`**: Years of formal education required.  
- **`LIX`**: Index using sentence and word length.  
- **`SMOG Index`**: Based on polysyllabic word frequency.  
- **`RIX`**: Long words (7+ letters) per 100 words.  
- **`Dale–Chall Index`**: Based on unfamiliar words from a standard list.

### Other Linguistic Features

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

---

## Blockchain-Related Features

These features capture blockchain and crypto ecosystem signals relevant to each article:

### Temporal

- `days_since_epoch`: Days elapsed since article publication

### Market Indicators

For each token (`BTC`, `ETH`, `OP`, `USDT`, `USDC`, `DAI`) at the publication date:

- `open_<token>_usd`: Opening price  
- `last_<token>_usd`: Closing price  
- `max_<token>_usd`: Daily maximum  
- `min_<token>_usd`: Daily minimum  
- `vol_<token>`: Trading volume  
- `var%_<token>`: Daily % price change  

### Blockchain Activity

- `daily_transactions_optimism`: Daily tx count on Optimism  
  ↳ Source: [Optimism Etherscan Chart](https://optimistic.etherscan.io/chart/tx)  
- `eth_active_addresses_total`: Total active Ethereum addresses  
- `eth_active_addresses_sender`: Active senders on Ethereum  
- `eth_active_addresses_receiver`: Active receivers on Ethereum  
- `optimism_active_addresses_total`: Total active addresses on Optimism  
  ↳ Source: [Ethereum Etherscan Chart](https://etherscan.io/chart/active-address)

### Author Wallet Features

- `author_ether_balance`: ETH balance of author's wallet  
- `author_transactions_number`: Total blockchain transactions by author

### Author Platform Activity

- `authorPostCount`: Number of published articles  
- `authorTotalSales`: Number of sold Writing NFTs  
- `authorTotalRevenue`: Total revenue (in ETH) from NFT sales

### External Signals

- `week_google_searches_<x>`: Google Trends score (1–100) during publication week  
  Terms include: `nft`, `crypto`, `bitcoin`, `ethereum`, `optimism`

---
