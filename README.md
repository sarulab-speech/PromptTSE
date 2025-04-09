# PromptTSE Dataset
We introduce the PromptTSE dataset, a new corpus designed for language-queried target speech extraction. This corpus is derived from LibriTTS-P [1] and EARS [2], and consists of triplets of target speech, interference speech, and speech mixtures, along with metadata.

# How to use PromptTSE
**PromptTSE is available from [here](https://huggingface.co/datasets/sarulab-speech/PromptTSE/tree/main)**

## Dataset Structure
```
.
├── metadata.json
└── wav
    ├── train
    │   ├── 100
    │   │   ├── train_000004_interf.wav
    │   │   ├── train_000004_mixed.wav
    │   │   ├── train_000004_target.wav
    │   │   └── ...
    │   └── ...
    ├── val
    │   └── ...
    └── test
        └── ...
```

## Metadata
Each key in metadata corresponds to a specific type of information as described below.
| Name               | Description                                                    |
|--------------------|----------------------------------------------------------------|
| uid                | Utterance ID                                                   |
| wav_path           | Path to the wav file                                           |
| clue               | Clue used in our experiment (described below)                  |
| params             | SNR [dB] and duration [sec]                                    |
| speech_label       | Clue related to the target speech (described below)            |

The `clue` contains the following information:
| Name               | Description                                                    |
|--------------------|----------------------------------------------------------------|
| prompt             | Prompt used in PNTP-TSE                                        |
| enrollment         | Path to the enrollment speech                                  |
| info               | Text prompt describing gender, pitch, speed, and loudness      |

The `speech_label` contains the following information for both target and interference:
| Name               | Description                                                    |
|--------------------|----------------------------------------------------------------|
| transcription      | Transcription                                                  |
| corpus             | Corpus to which the speech belongs                             |
| spk                | Speaker ID in the original corpus                              |
| file_name          | Path in the original corpus                                    |
| style_feature      | Statistics of pitch, loudness, and speed                       |
| duration           | Duration in seconds                                            |

# References
[1] M. Kawamura, R. Yamamoto, Y. Shirahata, T. Hasumi, and K. Tachibana, “LibriTTS-P: A corpus with speaking style and speaker identity prompts for text-tospeech and style captioning,” in Proc. INTERSPEECH, Kos, Greek, 2024, pp. 1850–1854.

[2] J. Richter, Y.-C. Wu, S. Krenn, S. Welker, B. Lay, S. Watanabe, A. Richard, and T. Gerkmann, “EARS: An anechoic fullband speech dataset benchmarked for speech enhancement and dereverberation,” in Proc. INTERSPEECH, Kos, Greek, 2024, pp. 4873–4877.
