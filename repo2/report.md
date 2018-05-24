##<コード>  

###sigmoid関数とsoftmax関数の実装

    import numpy as np

    def sigmoid(x):
        ans = 1 / (1 + np.exp(-x))
        return ans

    def softmax(x):
        x = np.exp(x)
        total = np.sum(x)
        y = x / total
        return y

###３層マルチパーセプトロンのNNの実装

    import numpy as np


    def sigmoid(x):
    ans = 1 / (1 + np.exp(-x))
    return ans


    def softmax(x):
        x = np.exp(x)
        total = np.sum(x)
        y = x / total
        return y


    def identity_function(x):
        return x


    def init_network():
        network = {}
        network['W1'] = np.array([[0.1, 0.3, 0.5], [0.2, 0.4, 0.6]])
        network['b1'] = np.array([0.1, 0.2, 0.3])
        network['W2'] = np.array([[0.1, 0.4], [0.2, 0.5], [0.3, 0.6]])
        network['b2'] = np.array([0.1, 0.2])
        network['W3'] = np.array([[0.1, 0.3], [0.2, 0.4]])
        network['b3'] = np.array([0.1, 0.2])
        return network

    def forword(network, x):
        # layer 1
        W1 = network['W1']
        b1 = network['b1']
        a1 = np.dot(x, W1) + b1
        z1 = sigmoid(a1)

        # layer 2
        W2 = network['W2']
        b2 = network['b2']
        a2 = np.dot(z1, W2) + b2
        z2 = sigmoid(a2)

        # layer 3
        W3 = network['W3']
        b3 = network['b3']
        a3 = np.dot(z2, W3) + b3
        y = identity_function(a3)

        return y

    network = init_network()
    x = np.array([1.0, 0.5])
    y = forword(network, x)
    print(y)

###バッチ処理の行い方

    import numpy as np
    import random

    def sigmoid(x):
        ans = 1 / (1 + np.exp(-x))
        return ans

    def identity_function(x):
        return x

    def init_network():
        network = {}
        network['W1'] = np.array([[0.1, 0.3, 0.5], [0.2, 0.4, 0.6]])
        network['b1'] = np.array([0.1, 0.2, 0.3])
        network['W2'] = np.array([[0.1, 0.4], [0.2, 0.5], [0.3, 0.6]])
        network['b2'] = np.array([0.1, 0.2])
        network['W3'] = np.array([[0.1, 0.3], [0.2, 0.4]])
        network['b3'] = np.array([0.1, 0.2])
        return network

    def forword(network, x):
        # layer 1
        W1 = network['W1']
        b1 = network['b1']
        a1 = np.dot(x, W1) + b1
        z1 = sigmoid(a1)

        # layer 2
        W2 = network['W2']
        b2 = network['b2']
        a2 = np.dot(z1, W2) + b2
        z2 = sigmoid(a2)

        # layer 3
        W3 = network['W3']
        b3 = network['b3']
        a3 = np.dot(z2, W3) + b3
        y = identity_function(a3)

        return y

    network = init_network()
    batch_size = 16
    x = np.random.rand(1000, 2)
    for i in range(0, len(x), batch_size):
        x_batch = x[i:i+batch_size]
        y_batch = forword(network, x_batch)
        print("batch : %d" % i)
        print(y_batch)

##<感想>
今回は前回と比較して内容が濃くなっていた。　　
実装に関しては復習ではあったものの
確実に合っているという確証がないので、
いい復習になった。
次回も思い出しながら　　
取り組んでいきたい。

##<参考文献>
教材: 第三回 情報学工房　　
　　: ゼロから作るDeep Learning
