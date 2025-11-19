# Instagram-fake-profile-detection
A machine learning–based tool that analyzes public Instagram profiles, extracts key features, and predicts whether an account is suspicious or likely fake using a trained classification model.

Automated tool that fetches public Instagram profile metadata and predicts a suspiciousness score using a saved ML pipeline (ig_auth_pipeline.pkl).
Detects likely fake/bot accounts and returns a probability, a human-readable label, and brief heuristic reasons.

🔎 Project Overview

This repository contains a lightweight pipeline that:
1.Accepts an Instagram profile URL or @username.
2.Uses instagrapi to fetch public profile metadata (requires an Instagram login session).
Extracts deterministic features from the profile.
3.Aligns features to a saved preprocessing + classifier pipeline (ig_auth_pipeline.pkl).
4.Outputs a suspiciousness probability and a short interpretation.
This is the codebase used for a research/project demo on Instagram fake-account detection.

⚠️ Important notes

1.Only public profile metadata is used. Private accounts are rejected.
2.The project requires an Instagram login (handled via instagrapi) to fetch profile metadata reliably. Session is stored locally and reused.
3.You must have a trained model pipeline stored as ig_auth_pipeline.pkl (see Model & Training).
4.Respect Instagram Terms of Service and user privacy. Use this for research/moderation only.

Features

1.Username normalization and validation
2.Robust session handling (login, 2FA, challenge flow)
3.Deterministic feature extraction: has_profile_picture, username_length, fullname_words, fullname_length, name_equals_username, description_length, external_url_present, is_private, num_posts, num_followers, num_following, followers_to_following_ratio, log_followers
4.Preprocessing + classifier inference from a serialized pipeline
5.Simple interpretability: LOW / MEDIUM / HIGH suspicion buckets + 1–2 short reasons
6.Safe fallbacks and error messages for private/invalid accounts and login failures
