# Don’t Stop Pretraining: Adapt Language Models to Domains and Tasks
[paper](https://www.aclweb.org/anthology/2020.acl-main.740.pdf)
[code](https://github.com/allenai/dont-stop-pretraining)

## Contents
* Classification을 in-domain과 different task에 대해서 수행할 때, 어떻게 pre-train하고 fine-tuning을 하면 좋은지를 실험적으로 비교
  * general domain으로 학습 한 뒤에 in-domain 데이터 셋으로 추가 MLM 학습
  * 마지막으로 task에 대해 학습
* ROBERT 네트워크를 기반으로 함

## Results
* ROBERT 네트워크를 in-domain 데이터셋으로 pre-training을 계속한 뒤, fine-tuning할 경우 성능의 향상이 크게 생김 - 과학 저널, 메디컬 글 처럼 general domain과 차이가 큰 경우에 향상 폭이 훨씬 큼
* 다른 