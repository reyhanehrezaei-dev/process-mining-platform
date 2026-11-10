# Model artifacts and prediction setup

The project integrates model code authored by teammates for:

- **Outcome classification:** ensemble models (tree, logistic regression, random forest)
- **Next activity:** LSTM sequence model
- **Remaining time:** LSTM regression model

The integrated inference layer is in `prediction/services.py`, using model and preprocessing classes from `prediction/`.

The original archive includes multiple copies of model binaries and large event logs. The public starter deliberately **omits trained model artifacts** to avoid distributing unreviewed datasets, serialized Python objects, weights or duplicate binaries. This means that the prediction endpoints will not provide real inference until compatible artifacts are installed.

The integration expects `prediction/trained_models/` with a preprocessor and model subfolders such as `ensemble/` and `lstm/`. See `prediction/services.py` for exact filenames and types. These are not downloadable from this repository.

**Do not load model files from an unknown source.** Pickle/joblib deserialization can execute code. Only use artifacts produced by your trusted teammates, and review dataset licenses / model rights before distributing them separately.

The published code also requires a compatible TensorFlow stack; the original team's run is not reproduced as part of this portfolio export.
