```mermaid
graph LR
    Speech_Synthesis_Orchestrator["Speech Synthesis Orchestrator"]
    Text_Preprocessing_Module["Text Preprocessing Module"]
    Core_Generative_Models["Core Generative Models"]
    Inference_Optimization_Engine["Inference Optimization Engine"]
    Audio_Synthesis_Module_Vocoder_["Audio Synthesis Module (Vocoder)"]
    Audio_Output_Utilities["Audio Output Utilities"]
    Model_Asset_Management["Model & Asset Management"]
    External_Interfaces["External Interfaces"]
    External_Interfaces -- "initiates synthesis requests to" --> Speech_Synthesis_Orchestrator
    Speech_Synthesis_Orchestrator -- "sends raw text to" --> Text_Preprocessing_Module
    Text_Preprocessing_Module -- "returns normalized text to" --> Speech_Synthesis_Orchestrator
    Speech_Synthesis_Orchestrator -- "sends processed text and requests intermediate codes/features from" --> Core_Generative_Models
    Core_Generative_Models -- "utilizes" --> Inference_Optimization_Engine
    Inference_Optimization_Engine -- "provides optimized model outputs back to" --> Core_Generative_Models
    Core_Generative_Models -- "returns intermediate codes/features and speaker embeddings to" --> Speech_Synthesis_Orchestrator
    Speech_Synthesis_Orchestrator -- "sends acoustic features to" --> Audio_Synthesis_Module_Vocoder_
    Audio_Synthesis_Module_Vocoder_ -- "returns raw audio waveform to" --> Speech_Synthesis_Orchestrator
    Speech_Synthesis_Orchestrator -- "sends raw audio waveform to" --> Audio_Output_Utilities
    Speech_Synthesis_Orchestrator -- "requests model/asset availability checks and initiates downloads from" --> Model_Asset_Management
    Model_Asset_Management -- "provides model assets and configurations to" --> Speech_Synthesis_Orchestrator
    External_Interfaces -- "triggers model export from" --> Core_Generative_Models
    click Speech_Synthesis_Orchestrator href "https://github.com/CodeBoarding/GeneratedOnBoardings/blob/main/ChatTTS/Speech_Synthesis_Orchestrator.md" "Details"
    click Text_Preprocessing_Module href "https://github.com/CodeBoarding/GeneratedOnBoardings/blob/main/ChatTTS/Text_Preprocessing_Module.md" "Details"
    click Core_Generative_Models href "https://github.com/CodeBoarding/GeneratedOnBoardings/blob/main/ChatTTS/Core_Generative_Models.md" "Details"
    click Inference_Optimization_Engine href "https://github.com/CodeBoarding/GeneratedOnBoardings/blob/main/ChatTTS/Inference_Optimization_Engine.md" "Details"
    click Audio_Synthesis_Module_Vocoder_ href "https://github.com/CodeBoarding/GeneratedOnBoardings/blob/main/ChatTTS/Audio_Synthesis_Module_Vocoder_.md" "Details"
    click Audio_Output_Utilities href "https://github.com/CodeBoarding/GeneratedOnBoardings/blob/main/ChatTTS/Audio_Output_Utilities.md" "Details"
    click Model_Asset_Management href "https://github.com/CodeBoarding/GeneratedOnBoardings/blob/main/ChatTTS/Model_Asset_Management.md" "Details"
    click External_Interfaces href "https://github.com/CodeBoarding/GeneratedOnBoardings/blob/main/ChatTTS/External_Interfaces.md" "Details"
```

[![CodeBoarding](https://img.shields.io/badge/Generated%20by-CodeBoarding-9cf?style=flat-square)](https://github.com/CodeBoarding/CodeBoarding)[![Demo](https://img.shields.io/badge/Try%20our-Demo-blue?style=flat-square)](https://www.codeboarding.org/demo)[![Contact](https://img.shields.io/badge/Contact%20us%20-%20contact@codeboarding.org-lightgrey?style=flat-square)](mailto:contact@codeboarding.org)

## Details

The ChatTTS architecture is structured as a comprehensive ML toolkit for text-to-speech synthesis, centered around a Speech Synthesis Orchestrator that manages the entire data flow. User interactions, whether via CLI, WebUI, or REST API, are handled by External Interfaces, which initiate synthesis requests. The input text first passes through the Text Preprocessing Module for normalization and tokenization. The processed text then enters the Core Generative Models (GPT, DVAE, and speaker embedding components), which transform it into acoustic features, with performance optimized by the Inference Optimization Engine. These acoustic features are subsequently converted into raw audio waveforms by the Audio Synthesis Module (Vocoder). The final audio is then managed by Audio Output Utilities for conversion and saving. Throughout the process, Model & Asset Management ensures that necessary model weights and configurations are loaded and available. Additionally, the External Interfaces also facilitate specialized operations like ONNX model export.

### Speech Synthesis Orchestrator [[Expand]](./Speech_Synthesis_Orchestrator.md)
The central control unit managing the entire text-to-speech pipeline. It orchestrates data flow from text input to final audio output, coordinating interactions between all core synthesis modules.


**Related Classes/Methods**:

- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/core.py" target="_blank" rel="noopener noreferrer">`ChatTTS.core`</a>


### Text Preprocessing Module [[Expand]](./Text_Preprocessing_Module.md)
Handles the initial processing of raw input text, including normalization, language detection, and tokenization, to prepare it for the generative models.


**Related Classes/Methods**:

- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/norm.py" target="_blank" rel="noopener noreferrer">`ChatTTS.norm`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/model/tokenizer.py" target="_blank" rel="noopener noreferrer">`ChatTTS.model.tokenizer`</a>


### Core Generative Models [[Expand]](./Core_Generative_Models.md)
Encompasses the primary neural network models responsible for transforming processed text into acoustic features and incorporating speaker characteristics (GPT-based text-to-code model, DVAE, and speaker embedding logic).


**Related Classes/Methods**:

- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/model/gpt.py" target="_blank" rel="noopener noreferrer">`ChatTTS.model.gpt`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/model/dvae.py" target="_blank" rel="noopener noreferrer">`ChatTTS.model.dvae`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/model/speaker.py" target="_blank" rel="noopener noreferrer">`ChatTTS.model.speaker`</a>


### Inference Optimization Engine [[Expand]](./Inference_Optimization_Engine.md)
A high-performance backend (likely inspired by vLLM) dedicated to optimizing the execution of the large language models within the Core Generative Models. It manages GPU memory, batching, and request scheduling for efficient throughput.


**Related Classes/Methods**:

- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/model/velocity/llm.py" target="_blank" rel="noopener noreferrer">`ChatTTS.model.velocity.llm`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/model/velocity/llm_engine.py" target="_blank" rel="noopener noreferrer">`ChatTTS.model.velocity.llm_engine`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/model/velocity/worker.py" target="_blank" rel="noopener noreferrer">`ChatTTS.model.velocity.worker`</a>


### Audio Synthesis Module (Vocoder) [[Expand]](./Audio_Synthesis_Module_Vocoder_.md)
The final stage of the synthesis pipeline, responsible for converting acoustic features into raw, audible audio waveforms using a vocoder (specifically, `vocos` integration).


**Related Classes/Methods**:

- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/core.py" target="_blank" rel="noopener noreferrer">`ChatTTS.core`</a>


### Audio Output Utilities [[Expand]](./Audio_Output_Utilities.md)
Provides utilities for handling, converting, and saving the synthesized audio data into various common formats (e.g., WAV, MP3).


**Related Classes/Methods**:

- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/tools/audio/pcm.py" target="_blank" rel="noopener noreferrer">`tools.audio.pcm`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/tools/audio/av.py" target="_blank" rel="noopener noreferrer">`tools.audio.av`</a>


### Model & Asset Management [[Expand]](./Model_Asset_Management.md)
Manages the lifecycle of model assets, including downloading necessary model weights and configuration files from remote sources, verifying their integrity, and loading configurations.


**Related Classes/Methods**:

- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/utils/dl.py" target="_blank" rel="noopener noreferrer">`ChatTTS.utils.dl`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/ChatTTS/config/config.py" target="_blank" rel="noopener noreferrer">`ChatTTS.config.config`</a>


### External Interfaces [[Expand]](./External_Interfaces.md)
Provides various interaction points for users and other applications to access the ChatTTS system, including command-line, web-based, RESTful API, and ONNX export functionalities.


**Related Classes/Methods**:

- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/examples/cmd/run.py" target="_blank" rel="noopener noreferrer">`examples.cmd.run`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/examples/web/webui.py" target="_blank" rel="noopener noreferrer">`examples.web.webui`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/examples/api/openai_api.py" target="_blank" rel="noopener noreferrer">`examples.api.openai_api`</a>
- <a href="git@github.com:2noise/ChatTTS.git/blob/main/temp/61f936eb8766444da3d6592b4973b108/examples/onnx/exporter.py" target="_blank" rel="noopener noreferrer">`examples.onnx.exporter`</a>




### [FAQ](https://github.com/CodeBoarding/GeneratedOnBoardings/tree/main?tab=readme-ov-file#faq)