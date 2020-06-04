# (Discrete) melody simiarlity
* 기존에는 dynamic programming 기반의 sequence alignment나 edit distance기반의 방법을 활용
    * similarity score를 계산하지 않거나 비교가 어려운 단점
    * computation cost가 크다는 단점
* 최근 deep metric learning 기반의 simimlarity learning이 제안 되었음
---
* [Learning Similarity Metrics for Melody Retrieval](http://archives.ismir.net/ismir2019/paper/000057.pdf)
    * Triplet loss를 활용한 metric learning을 하였으며, melody similarity를 위한 데이터셋을 제공함
    * [Meertens Tune Collections dataset](http://www.liederenbank.nl/mtc/)
        * 5세기에 걸친 monophonic으로 구성된 vocal 혹은 instrument 독일 음악으로 구성
        * MTC-FS-INST 2.0은 총 18109 melody를 가지고 있으며, 