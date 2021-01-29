# Deep Learning on Graphs : A Survey (Zhang, Cui and Zhu)

---
1. Introduction
    - Motivation
        irregular structure : non-Euclidean하여 좌표 / sequence를 정의하기 어려움
        heterogeneity and diversity : image, audio 보다 underlying distribution이 복잡하여 데이터셋의 다양성이 큼
        large-scale : node, edge의 수가 큰 문제가 많이 scalability가 중요함
    - Notations
        s_i : node i의 state (trained feature)
        f_i : node i의 embedding (initial feature, characteristic)
        f_ij : edge ij의 embedding
        m : message
        F, G : trainable parametric function (neural network)
        neighbor : order 1 neighbor
        A : graph adjency matrix
        D : graph degree matrix
        L : Laplacian matrix (D - A)
        P : transition matrix
        tilde : graph with self connection (A + I)
1. Graph Recurrent Neural Network
    - Node-level RNN (Graph NN, GNN, Scarselli)
        recursion : s_i = sum_neighbor(F(s_i, s_j, f_i, f_j, f_ij))
        Gated Graph Sequence NN (GGS-NN, Tarlow) : GRU와 같이 s_i(t) =  (1 - z(t))s_i(t - 1) + z(t)delta(t) where z(t), delta(t) = sum_neighbor(F(s_i, s_j, f_i, f_j, f_ij))과 같은 형태로 나타남
    - Graph-level RNN
        graph generation에서 두 RNN을 활용한 연구(You et al.) -> 하나의 RNN은 node 생성 및 state(s) 출력(node generator), 다른 RNN은 생성된 node와 기존의 nodes 사이의 연결관계 생성(edge generator)
        dynamic graph : 시간이 지남에 따라 변화하는 그래프(새로운 고객 혹은 제품이 추가되는 경우 등)
        Dynamic Graph NN (DGNN, Ma) : dynamic graph의 temporal 정보를 처리하기 위해 time-aware LSTM 활용
            * Time-aware LSTM(TLSTM,Baytas) : event 발생 사이의 시간을 feature로써 추가하여 hidden state / output 계산
2. Graph Convolution Network
    - Spectral Methods
        convolution : neighboring pixel / timeframe에 대해 sliding window를 사용해서 연산
        그런데 graph에서는 grid / coordinates가 정의되지 않아 convolution을 Fourier (spectral) domain에서 수행
        전체 Fourier domain을 활용할 경우 node 수 만큼의 eigenvector 활용 필요 --> not scalable --> Chebyshev GNN (ChevNet, Defferard)에서 k-th order까지의 spectral 활용하는 방법 제안
        Deep Graph Convolutional Network(DGCN, Kipf and Welling) : 1st order spectral만을 활용, max eigenvalue에 대한 가정 추가로 식을 단순화 함
            이 survey보다는 Kipf and Welling, Defferard를 읽는 것이 더 나을 듯?
        간단히 요약하자면 각 convolutional operation은 activation(D_tilde^-0.5 A_tilde D_tilde^-0.5 X theta)로 표현됨
        theta는 학습되는 파라미터
        D_tilde^-0.5 A_tilde D_tilde^-0.5 : layer, input에 따라 바뀌는 값이 아닌 graph에 따라 바뀌는 값(degree와 adjency에 따라) --> preprocessing 단계에서 미리 다 계산해놓기
        Neural FingerPrint (Neural FP, Duvenaud) : node의 degree에 따른 theta 학습 --> degree가 다르면 node를 임베딩하는 방식도 달라야한다! small graph에서는 잘 학습되나, scalable하지 않음
        PATCHY-SAN (Niepert) : node reordering을 통해 유사한 node끼리 가깝게 배치 후, 일반적 CNN과 유사하게 receptive field 정의, convolution
    - Diffusion CNN (DCNN, Atwood)
        'neighborhood' : diffusion-basis, 즉 transition probability로 정의함
        Out = activation(P^K X theta) (K : preset diffusion length)
        P^K 계산할 때에 time consuming
    - Message Passing NN (MPNN, Gilmer)
        Graph RNN과 유사해보임
        m_i(l+1) = sum_neighbor(F(h_il, h_jl, f_ij)) : message calculation
        h_i(l+1) = G^l(h_il, m_i(l+1)) : node update
        GraphSAGE (Hamilton)
            m_i(l+1) = AGGREGATE({h_jl for j in neighbor(i)}) : message calculation
            h_i(l+1) = activation(theta_l[concat(h_il, m_i(l+1))]) : node update
            AGGREGATE는 LSTM, elementwise mean, max-pooling 중 하나
        Mixture Model Network (MoNet, Monti)
            두 node들의 degree를 pseudo-coordinates로 활용 (u(i,j) = (D(i, i)^-0.5, D(j, j)^-0.5))
            Gaussian kernel with trainable mean and stdev 활용
        Graph Networks(Battanglia) : 3 sets of representations and messages, nodes, edges and the entire graph
    - Readout Operations
        node representation에서 graph representation으로 바꾸기 위한 aggregation 방법은 node order에 대한 invariance(statistics)가 제공되거나, 특정 규칙을 통한 node ordering(hierarchical clustering) 필요
    - Further Discussions
        - Attention
            Graph Attention Network (Velickovic) : node들의 key, query, value
            Heterogeneous Graph Attention Network (HAN, Wang) : semantic-level attention (node type 사이의 attention을 계산하고, node 사이의 attention과 aggregate해서 활용)
        - Residual / Skip Connection
            Kipf and Welling에서는 elementwise summation을 통한 residual connection 제시
            Column Network (CLN, Pham) : learnable weight(gate)로 residual과 delta 사이의 ratio 학습
            Personalized Propagation of Neural Predictions (PPNP, Klicpera) : initial input에 대한 residual connection 추가
            Jumping Knowledge Network (JKNet, Xu) : 이전 모든 layer들과 skip connection
        - Edge Features
            edge type을 활용하는 연구 (CLN 등)
            DCNN : edge를 두 node 사이의 node로 취급하여 edge feature / state 계산
            message passing에서도 edge message 활용하기도
        - Others
            neighborhood sampling
            theoretical analysis
3. Graph AutoEncoder
    Structure Deep Network Embedding (SDNE, Wang) : graph adjency에 대한 L2 reconstruction + Lapacian eigenmaps --> directly connected node들은 similar latent representation을 가져야 함을 학습함
    Graph Convolution Matrix Completion (GCMC, Berg) : Kipf and Welling의 GCN을 encoder / decoder로 활용
    Deep Recursive Network Embedding (DRNE, Tu) : LSTM으로 neighboring node vector들을 aggregation한 것과 node vector 사이의 L1 loss
    Graph2Gauss (G2G, Bojchevski) : node의 uncertainty를 표현하기 위해 node vector에 대한 직접적 모델링이 아닌 그 평균과 표준편차를 모델링
    VAE도 있음ㅎㅎ