# BikeEase AI Project Notes

## Progress Log

### Environment Setup
- Created conda environment `bikeease-ai`
- Installed dependencies:
  - `langchain`
  - `langchain-community`
  - `transformers`
  - `huggingface_hub`
  - `torch`
  - `notebook` (for Jupyter)
- Set up `bikeease-ai` as a Jupyter kernel

### GitHub Repo Setup
- Initialized local Git repo in `BikeEase` folder
- Created `.gitignore` (ignoring caches, checkpoints, env files, etc.)
- Added initial `README.md` with project description
- Prepared `requirements.txt` for dependencies

### Jupyter Notebook Setup
- Created notebook `BikeEase.ipynb`
- Added initial project overview in Markdown
- Verified kernel: **Python (bikeease-ai)**

### First Model Attempts
- **distilgpt2**  
  - Loaded successfully, but only echoed prompt (not instruction-tuned)
- **databricks/dolly-v2-3b**  
  - Required `trust_remote_code=True`  
  - Loaded but very slow on MacBook (large model ~6GB)  
  - Warning received about custom code (`instruct_pipeline.py`)
- **google/flan-t5-base**  
  - Chosen as main working model (fast, instruction-tuned, lightweight)  
  - Generated first persuasive ad successfully 🎉

### First Generated Ad
20% off this weekend!

BikeEase is a 24-gear mountain bike company. We offer a wide range of high-quality bikes that are built to last.

Whether you’re a beginner or an experienced biker, we have a bike for you. Our bikes can go on most bicycle trails and are easy to ride.

Come check out our selection of 24-gear mountain bikes this weekend. This offer is valid until 11:59 PM on Monday, April 2.


###  Improvements Implemented
- Switched from `max_length` to `max_new_tokens` for better control
- Added `temperature` and `top_p` for more creativity
- Used Flan-T5 for faster, instruction-following generation

###  Next Steps
- Add emojis, hashtags, and calls-to-action in prompt template
- Generate multiple ad variations per input
- Set up model comparison between Flan-T5, Dolly, and possibly GPT-Neo
- Store results in a CSV for later evaluation
- Experiment with few-shot prompting to align closer with BikeEase branding

---

### Current Work
- Running Dolly-v2-3B with a few-shot prompt:
  - Emojis, hashtags, and call-to-action included in examples
  - Using `temperature=0.8`, `top_p=0.9`, and `do_sample=True`
- Expecting better quality persuasive ads despite slower generation

###  Next Steps
- Generate 3–5 ad variations in one run for comparison
- Save generated ads to CSV for review
- Compare Dolly output with Flan-T5-Large or GPT-Neo if time permits
- Document pros/cons of each model for final homework submission

---

## Key Takeaways So Far
- Small models (distilgpt2) are too weak for marketing copy
- Instruction-tuned models (Flan, Dolly) are necessary for ad-style outputs
- Flan models are fast but ignore sampling → boring outputs
- Dolly is slow but supports creative sampling → likely best for assignment
- Few-shot prompting is essential to get ads with emojis/hashtags instead of literal instructions