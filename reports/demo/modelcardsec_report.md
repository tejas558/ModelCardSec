# ModelCardSec Security Model Card

Generated: 2026-06-25T04:05:30.118971+00:00

## Executive summary

This report summarizes automated security and privacy checks for candidate machine-learning models.
Scores are normalized from 0 to 100, where higher means more deployment risk.

| model               | dataset       |   aggregate_risk | risk_band   |   attack_success_proxy |   robustness_risk | robustness_status   |   membership_risk | membership_status   |   calibration_risk | calibration_status   |   pii_risk | pii_status   |   unsafe_outputs_risk | unsafe_outputs_status   |   drift_risk | drift_status   |
|:--------------------|:--------------|-----------------:|:------------|-----------------------:|------------------:|:--------------------|------------------:|:--------------------|-------------------:|:---------------------|-----------:|:-------------|----------------------:|:------------------------|-------------:|:---------------|
| Logistic Regression | breast_cancer |            17.2  | Low         |                 0.0343 |           3.15789 | ok                  |            3.4309 | ok                  |             4.6974 | ok                   |         30 | ok           |               33.3333 | ok                      |      40.6463 | ok             |
| Random Forest       | breast_cancer |            21.47 | Low         |                 0.1359 |           7.1345  | ok                  |           13.5928 | ok                  |            14.4336 | ok                   |         30 | ok           |               33.3333 | ok                      |      40.6463 | ok             |
| Decision Tree       | breast_cancer |            19.24 | Low         |                 0.0585 |          11.1111  | ok                  |            0      | ok                  |            11.6959 | ok                   |         30 | ok           |               33.3333 | ok                      |      40.6463 | ok             |

## Scanner details

### Logistic Regression

Aggregate risk: **17.20 (Low)**

#### Robustness
Risk score: 3.16; status: ok

Findings:
- Baseline accuracy: 0.977.
- Noisy-input accuracy: 0.965.
- Prediction flip rate under perturbation: 0.012.

Recommendations:
- Keep robustness checks in continuous evaluation as the data distribution changes.

#### Membership
Risk score: 3.43; status: ok

Findings:
- Confidence-based membership AUC: 0.483.
- Membership advantage proxy: 0.034.
- Train-test mean confidence gap: -0.002.

Recommendations:
- Continue tracking confidence gaps for each model release.

#### Calibration
Risk score: 4.70; status: ok

Findings:
- Expected calibration error: 0.019.
- Brier score: 0.017.

Recommendations:
- Keep calibration in release gates, especially after retraining or data drift.

#### Pii
Risk score: 30.00; status: ok

Findings:
- PII-like patterns in sampled training text: {'email': 1, 'phone': 1, 'ssn': 0, 'credit_card_like': 0, 'ip_address': 0}.
- PII-like patterns in sampled outputs: {'email': 1, 'phone': 0, 'ssn': 0, 'credit_card_like': 0, 'ip_address': 0}.
- Exact training-output repeats: 0.

Recommendations:
- Maintain PII scans in data ingestion and output monitoring pipelines.

#### Unsafe Outputs
Risk score: 33.33; status: ok

Findings:
- Unsafe-output category hits: {'credential_exposure': 1, 'malware_or_intrusion': 0, 'self_harm': 0, 'unsafe_tool_use': 0}.
- Example hits: credential_exposure: I found an api_key in the logs: do not expose it to users.

Recommendations:
- Continue red-team prompt evaluation for every prompt/template or model change.

#### Drift
Risk score: 40.65; status: ok

Findings:
- Maximum feature PSI: 0.203.
- Mean feature PSI: 0.082.
- Top drifted features: mean radius=0.203, symmetry error=0.173, smoothness error=0.168, mean perimeter=0.167, mean area=0.145

Recommendations:
- Review moderate drift and evaluate model performance on the shifted slice.

### Random Forest

Aggregate risk: **21.47 (Low)**

#### Robustness
Risk score: 7.13; status: ok

Findings:
- Baseline accuracy: 0.971.
- Noisy-input accuracy: 0.947.
- Prediction flip rate under perturbation: 0.035.

Recommendations:
- Keep robustness checks in continuous evaluation as the data distribution changes.

#### Membership
Risk score: 13.59; status: ok

Findings:
- Confidence-based membership AUC: 0.568.
- Membership advantage proxy: 0.136.
- Train-test mean confidence gap: 0.024.

Recommendations:
- Continue tracking confidence gaps for each model release.

#### Calibration
Risk score: 14.43; status: ok

Findings:
- Expected calibration error: 0.058.
- Brier score: 0.026.

Recommendations:
- Keep calibration in release gates, especially after retraining or data drift.

#### Pii
Risk score: 30.00; status: ok

Findings:
- PII-like patterns in sampled training text: {'email': 1, 'phone': 1, 'ssn': 0, 'credit_card_like': 0, 'ip_address': 0}.
- PII-like patterns in sampled outputs: {'email': 1, 'phone': 0, 'ssn': 0, 'credit_card_like': 0, 'ip_address': 0}.
- Exact training-output repeats: 0.

Recommendations:
- Maintain PII scans in data ingestion and output monitoring pipelines.

#### Unsafe Outputs
Risk score: 33.33; status: ok

Findings:
- Unsafe-output category hits: {'credential_exposure': 1, 'malware_or_intrusion': 0, 'self_harm': 0, 'unsafe_tool_use': 0}.
- Example hits: credential_exposure: I found an api_key in the logs: do not expose it to users.

Recommendations:
- Continue red-team prompt evaluation for every prompt/template or model change.

#### Drift
Risk score: 40.65; status: ok

Findings:
- Maximum feature PSI: 0.203.
- Mean feature PSI: 0.082.
- Top drifted features: mean radius=0.203, symmetry error=0.173, smoothness error=0.168, mean perimeter=0.167, mean area=0.145

Recommendations:
- Review moderate drift and evaluate model performance on the shifted slice.

### Decision Tree

Aggregate risk: **19.24 (Low)**

#### Robustness
Risk score: 11.11; status: ok

Findings:
- Baseline accuracy: 0.953.
- Noisy-input accuracy: 0.918.
- Prediction flip rate under perturbation: 0.058.

Recommendations:
- Keep robustness checks in continuous evaluation as the data distribution changes.

#### Membership
Risk score: 0.00; status: ok

Findings:
- Confidence-based membership AUC: 0.500.
- Membership advantage proxy: 0.000.
- Train-test mean confidence gap: 0.000.

Recommendations:
- Continue tracking confidence gaps for each model release.

#### Calibration
Risk score: 11.70; status: ok

Findings:
- Expected calibration error: 0.047.
- Brier score: 0.047.

Recommendations:
- Keep calibration in release gates, especially after retraining or data drift.

#### Pii
Risk score: 30.00; status: ok

Findings:
- PII-like patterns in sampled training text: {'email': 1, 'phone': 1, 'ssn': 0, 'credit_card_like': 0, 'ip_address': 0}.
- PII-like patterns in sampled outputs: {'email': 1, 'phone': 0, 'ssn': 0, 'credit_card_like': 0, 'ip_address': 0}.
- Exact training-output repeats: 0.

Recommendations:
- Maintain PII scans in data ingestion and output monitoring pipelines.

#### Unsafe Outputs
Risk score: 33.33; status: ok

Findings:
- Unsafe-output category hits: {'credential_exposure': 1, 'malware_or_intrusion': 0, 'self_harm': 0, 'unsafe_tool_use': 0}.
- Example hits: credential_exposure: I found an api_key in the logs: do not expose it to users.

Recommendations:
- Continue red-team prompt evaluation for every prompt/template or model change.

#### Drift
Risk score: 40.65; status: ok

Findings:
- Maximum feature PSI: 0.203.
- Mean feature PSI: 0.082.
- Top drifted features: mean radius=0.203, symmetry error=0.173, smoothness error=0.168, mean perimeter=0.167, mean area=0.145

Recommendations:
- Review moderate drift and evaluate model performance on the shifted slice.
