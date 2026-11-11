# 원하는 포즈로 이미지 만드는 도구

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/k-im-rose/pose-image-tool/blob/main/pose_tool.ipynb)

## 도구 설명
- 참조 사진에서 OpenPose로 관절 뼈대를 뽑고, 그 뼈대를 포즈 조건으로 넣어 **같은 자세의 다른 인물·장면**을 만듭니다.
- 모델은 FLUX.2-klein 4B(GGUF Q4, Apache 2.0)이고 ComfyUI에서 돌립니다. 교안의 FLUX.2-klein 4B Colab 노트가 출발점입니다.
- FLUX.2에는 공식 ControlNet이 없어서, 뼈대 그림을 klein의 **참조 이미지(ReferenceLatent)** 로 넣고 프롬프트로 "같은 자세로" 지시합니다.
- 비교용으로 SD 1.5 + OpenPose ControlNet 셀도 부록에 있습니다.

```
참조 사진 → OpenPose → 뼈대 그림 ─┐
                                  ├→ FLUX.2-klein 4B → 같은 자세의 새 이미지
프롬프트 ─────────────────────────┘
```

## 사용법
1. 위 **Open in Colab** 버튼(또는 GitHub의 `pose_tool.ipynb`)으로 노트를 엽니다.
2. [런타임 → 런타임 유형 변경 → T4 GPU]로 바꿉니다.
3. 셀을 위에서부터 순서대로 실행합니다: 설치 → 모델 다운로드 → 서버 실행 → 사진 올리기 → **포즈 추출 → 생성 → 저장**.
4. 마지막 셀이 `samples/` 와 `prompts.md` 를 zip으로 내려 줍니다.

## 폴더 구조
```
pose-image-tool/
├── README.md          # 이 문서
├── pose_tool.ipynb    # Colab 튜토리얼 노트 (핵심)
├── samples/
│   ├── pose_01.png            # 참조로 쓴 포즈 사진
│   ├── pose_01_skeleton.png   # OpenPose가 뽑은 뼈대
│   ├── output_01.png          # 같은 자세로 만든 결과
│   ├── output_01_nopose.png   # 비교: 포즈 조건 없이 같은 프롬프트
│   ├── expA_*.png             # 실험 A: 같은 포즈, 다른 프롬프트
│   └── expB_*.png             # 실험 B: 다른 포즈, 같은 프롬프트
└── prompts.md         # 테스트에 쓴 프롬프트·시드·설정 기록 (노트가 자동 생성)
```

## 테스트 결과
<!-- 직접 실행하고 관찰한 결과로 채웁니다 -->
- 포즈 1: (자세) → 프롬프트: … → 결과: …
- 포즈 2: (자세) → 프롬프트: … → 결과: …

## 한계
<!-- 직접 실행하고 관찰한 결과로 채웁니다 -->
- …

## 라이선스 메모
- FLUX.2-klein 4B는 Apache 2.0이라 상업 이용도 됩니다. 단 결과물 속 타인의 초상·저작물 권리까지 해결해 주지는 않습니다.
- 같은 이름의 FLUX.2-klein 9B는 비상업 전용입니다.
- `samples/` 의 참조 사진은 본인이 찍은 사진입니다.
