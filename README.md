# Preventing-Brigading-in-Reddit

A comprehensive approach to detect and prevent brigading on Reddit using graph-based modeling, anomaly detection, and machine learning techniques while respecting Reddit's terms of service and user privacy.

  

Reddit Hyperlinks Dataset from Stanford: https://snap.stanford.edu/data/soc-RedditHyperlinks.html

  

### Properties

- **SOURCE_SUBREDDIT**: Origin community

- **TARGET_SUBREDDIT**: Destination community

- **POST_ID**: Unique post identifier

- **TIMESTAMP**: Temporal information

- **LINK_SENTIMENT**: Sentiment score (-1, 0, 1)

- **PROPERTIES**: 80+ dimensional feature vector containing user behavior metrics

  

## Detection Framework

  

### 1. Graph-Based Modeling

  

#### Network Construction

- **Nodes**: Subreddits, Posts, Users (inferred from patterns)

- **Edges**: Cross-posting relationships, temporal sequences, sentiment flows

- **Edge Weights**: Based on frequency, sentiment alignment, and temporal proximity

  

#### Graph Features Extracted

- **Centrality Measures**:

- Betweenness centrality (identifies bridge communities)

- Degree centrality (identifies highly connected nodes)

- Eigenvector centrality (identifies influential communities)

- **Structural Features**:

- Clustering coefficient

- Community modularity

- Path lengths between subreddits

  

### 2. Brigading Detection Algorithms

  

#### A. Temporal Pattern Analysis

- Burst detection in cross-posting activity

- Synchronous posting patterns across multiple subreddits

- Abnormal activity spikes in specific time windows

  

#### B. Sentiment Coordination Detection

- Analyze sentiment distribution patterns

- Detect unusual sentiment unanimity

- Identify rapid sentiment shifts

  

#### C. Community Detection for Coordinated Groups

- **Louvain Algorithm**: For detecting tightly connected subreddit clusters

- **Girvan-Newman**: For hierarchical community structure

- **DBSCAN**: For identifying dense regions of activity

  

### 3. Feature Engineering

  

Key features extracted from the 80+ dimensional properties vector:

  

#### Behavioral Signatures

- Voting velocity (votes per unit time)

- Comment-to-post ratios

- Cross-subreddit activity frequency

- Account age and karma distribution

- Activity time patterns

  

#### Coordination Indicators

- Similar property vector patterns across posts

- Synchronized feature changes

- Anomalous feature combinations

  

### 4. Machine Learning Models

  

#### Supervised Learning

- **Models**: Random Forest / Gradient Boosting

- **Features**: Graph centrality, temporal features, sentiment features, properties vector components

  

#### Unsupervised Anomaly Detection

- **Models**: Isolation Forest / One-Class SVM

- **Purpose**: Detect novel brigading patterns

  

#### Deep Learning Approach

- **Model**: Graph Neural Network (GNN)

- **Architecture**:

- Graph Convolutional Network layers

- Attention mechanisms for temporal modeling

- Multi-task learning

  

<!--

## Implementation Strategy

  

### Phase 1: Data Preprocessing

1. Parse properties vector into meaningful features

2. Create temporal features (hour, day, week patterns)

3. Engineer graph-based features

4. Handle missing values and outliers

  

### Phase 2: Graph Construction

1. Build subreddit-to-subreddit network

2. Add temporal edges for sequential analysis

3. Calculate network metrics and community structures

  

### Phase 3: Model Development

1. Train baseline models (supervised)

2. Develop anomaly detection models

3. Implement ensemble methods

4. Fine-tune hyperparameters

  

### Phase 4: Validation and Testing

1. Cross-validation on historical data

2. Temporal split validation

3. Performance metrics evaluation

4. False positive analysis -->

  

## Prevention Strategies

  

### Rate Limiting Implementation

  

The system implements dynamic rate limiting based on detected brigading severity:

  

**Threshold-Based Restrictions**:

- **High Severity Detection** (Above upper threshold):

- Temporary 24-hour posting restrictions for identified user groups

- Immediate cross-post blocking between flagged subreddits

  

- **Medium Severity Detection**:

- Graduated cooldown periods (30-minute delays between posts)

- Reduced visibility for suspicious cross-posts

- Additional CAPTCHA verification requirements

  

**Implementation Logic**:

The rate limiting system activates when the system detects:

- Coordinated activity patterns exceeding platform norms

- Rapid cross-posting from single sources

- Unusual sentiment coordination across accounts

- Abnormal voting velocity patterns

  

The restrictions automatically scale with:

1. **Brigading Confidence Score** (higher scores → stronger limits)

2. **Historical Behavior** (repeat offenders receive stricter limits)

3. **Community Vulnerability** (new/small subreddits get earlier protection)

  

**Safeguards**:

- Gradual escalation to minimize false positives

- Transparent user notifications for all applied limits

- Manual override capability for moderators

  

## Conclusion

  

This project delivers a multi-layered defense against Reddit brigading through:

  

✅ **Graph-powered detection** – Uncovering hidden coordination patterns

✅ **ML-driven analysis** – Identifying both known and novel attack vectors

✅ **Ethical enforcement** – Balancing platform security with user rights

  

By combining network science, anomaly detection, and responsible moderation tools, we provide a framework that:

- Respects Reddit's API policies and user privacy

- Adapts to evolving brigading tactics

- Enhances trust in community-driven discussions

  

## Licence [[MIT](./LICENCE)]