# Distributed Text Classification

DeepSpeed 분류 학습 예제와 ICL 튜닝 학습기를 같은 모델 패키지로 묶었습니다. 두 학습 흐름은 별도 진입점으로 유지합니다.

## 코드 구조

| 경로 | 역할 |
|---|---|
| `distributed_classification/models/classification_model.py` | 공통 Transformer 분류 모델 |
| `distributed_classification/train_example.py` | 기본 분산 학습 예제 |
| `distributed_classification/train_classifier.py` | ICL 튜닝 학습 흐름 |
| `distributed_classification/configuration.py` | 명시적으로 전달한 실행 파일 로드 |

## 실행

```bash
pip install -e ".[runtime]"
deepspeed --help
```

실제 launcher는 DeepSpeed입니다. `deepspeed --module distributed_classification.train_classifier --config /path/to/execution.yaml`로 실행합니다. `models`, `ds_configs`, 데이터 입력과 학습 옵션은 각 진입점이 읽습니다. 구형 Transformers·datasets API를 사용하는 코드이므로 학습 환경의 버전 호환성을 확인해야 합니다.

## Source and license

See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for project origins and third-party licenses.
