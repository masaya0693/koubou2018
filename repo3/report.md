##<コード>

###Softmax with loss の実装

    class SoftmaxWithLoss:

        def __init__(self):
            self.loss = None
            self.y = None
            self.x = None

        def forward(self, x, t):
            self.t = t
            self.y = softmax(x)
            # forward
            self.loss = cross_entropy_error(self.y, self.t)
            return self.loss

        def backward(self, dout):
            # backward
            batch_size = self.t.shape[0]
            dx = (self.y - self.t) / batch_size
            return dx

###Two layer net の勾配の確認

    W1:2.685727285818323e-13
    b1:1.001591171112537e-12
    W2:8.748776260739111e-13
    b2:1.2034818003270332e-10

    
###Two layer net の実行結果

    epoc: 0
    train: 0.103800, test: 0.104800
    epoc: 1
    train: 0.901150, test: 0.901800
    epoc: 2
    train: 0.922133, test: 0.924500
    epoc: 3
    train: 0.936617, test: 0.934700
    epoc: 4
    train: 0.941483, test: 0.939300
    epoc: 5
    train: 0.950517, test: 0.948300
    epoc: 6
    train: 0.954933, test: 0.952200
    epoc: 7
    train: 0.959167, test: 0.955800
    epoc: 8
    train: 0.963567, test: 0.960800
    epoc: 9
    train: 0.965083, test: 0.961800
    epoc: 10
    train: 0.969900, test: 0.965200
    epoc: 11
    train: 0.970217, test: 0.965500
    epoc: 12
    train: 0.971933, test: 0.966900
    epoc: 13
    train: 0.975367, test: 0.967300
    epoc: 14
    train: 0.974683, test: 0.968300
    epoc: 15
    train: 0.977683, test: 0.969500
    epoc: 16
    train: 0.978467, test: 0.970600

##<感想>
今回の講義では、実際に２層のNNを用いた学習を行った。  
pycharmのチュートリアルに関しても教えて頂いたので、  
実践していきたい。  

##<参考文献>
教材: 第四回 情報学工房  
　　: ゼロから作るDeep Learning