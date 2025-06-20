# Zero-Shot NER with Gemini 1.5 Flash

This repository implements three zero-shot Named Entity Recognition (NER) methods from Xie et al.'s paper ["Zero-Shot Information Extraction via Chatting with ChatGPT"](https://arxiv.org/abs/2302.10205) using Gemini 1.5 Flash by slightly modifying prompts to be single turn and, hence, minimizing cost.

## Methods Implemented

1. **Decomposed QA**  
   - Single-turn extraction of all entity types simultaneously
   - Improved efficiency over original paper's multi-turn approach
   - Uses JSON output format for structured responses

2. **Tool-Augmented**  
   - Incorporates spaCy-generated syntactic features (POS tags, dependency trees)
   - Follows "analyze then extract" logic from the paper
   - Maintains single-turn execution for efficiency

3. **Self-Consistency**  
   - Implements two-stage majority voting for entity mentions and types
   - Uses 3 samples with temperature=0.7 for diversity
   - Applies >50% agreement thresholds for robust predictions

## Key Features

- Processed CoNLL-2003 dataset with proper train/dev/test splits
- Comprehensive evaluation metrics (Precision, Recall, F1)
- Detailed error visualization with color-coded entities
- Rate limiting and adaptive backoff for API stability
- Interactive Jupyter notebook with progress tracking

## Results

Method | Precision | Recall | F1
-------|-----------|--------|----
Decomposed-QA | 0.565 | 0.765 |0.650
Tool-Augmented | 0.520 | 0.750 | 0.614
Self-Consistency | 0.584 | 0.765 | 0.662


## Requirements

- Python 3.8+
- Gemini API key
- spaCy (`en_core_web_sm`)
- seqeval
- pandas
- requests

## Note

The free tier Gemini API has rate limits (15 requests/minute). For full evaluations, consider:
1. Using a paid API tier
2. Running evaluations in smaller batches
3. Caching responses for development

## Acknowledgments

Based on methods from:  
Xie et al. "Zero-Shot Information Extraction via Chatting with ChatGPT" (2023)# Cheap_zero_shot_NER