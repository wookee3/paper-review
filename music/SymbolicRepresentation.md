# Symbolic representation
1. pianoroll
   * (num. of pitches * timelen) 형태의 binary matrix로 각 시점에 어떤 pitch가 연주되고 있는지 표현
     * 장점
       * polyphonic도 쉽게 표현 가능
       * binary라서 cnn과 같은 스타일에 적용 쉬움
     * 단점
       * onset을 따로 표현하지 않기 때문에 똑같은 pitch의 반복을 표현하는 리듬이 사라짐

2. MIDI symbolic
   * midi에서 음을 표현하는 onset, offset, timeshift, velocity를 활용해서 token으로 변환
   * 장점
     * polyphonic도 쉽게 표현 가능
     * 음의 세기도 표현이 가능 
   * 단점
     * 매 timestep이 표현하는 것이 시간이 아니라서 음악의 특징인 강박, 약박과 같은 특징을 표현하지 못함 (음악의 구조적 특징 반영의 어려움) 
     * sequence의 길이가 길어짐

3. [REMI](https://arxiv.org/pdf/2002.00212.pdf)

4. [Compound word](https://arxiv.org/pdf/2101.02402.pdf)

5. Rhythm, pitch disentangled representation
   * 이를 위해 사용하는 방법으로는 여러가지가 있는데 그 중 대표적이고 활용 가능성이 높은 2가지를 정리

6. Ours

7. 기타
   * [GuitarTab modeling](https://arxiv.org/pdf/2008.01431.pdf)
