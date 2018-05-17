
<コード>

import numpy as np


def AND(x1, x2):
    x = np.array([x1, x2])
    w = np.array([0.5, 0.5])
    b = -0.7
    y = np.sum(w * x) + b
    if y <= 0:
        return 0
    else:
        return 1


def NAND(x1, x2):
    x = np.array([x1, x2])
    w = np.array([-0.5, -0.5])
    b = 0.7
    y = np.sum(w * x) + b
    if y <= 0:
        return 0
    else:
        return 1


def OR(x1, x2):
    x = np.array([x1, x2])
    w = np.array([0.5, 0.5])
    b = -0.2
    y = np.sum(w * x) + b
    if y <= 0:
        return 0
    else:
        return 1


def XOR(x1, x2):
    s1 = NAND(x1, x2)
    s2 = OR(x1, x2)
    y = AND(s1, s2)
    return y

if __name__ == "__main__":
    print("AND")
    for xs in [(0, 0), (1, 0), (0, 1), (1, 1)]:
        out = (AND(xs[0], xs[1]))
        print(str(xs) + " -> " + str(out))

    print()
    print("NAND")
    for xs in [(0, 0), (1, 0), (0, 1), (1, 1)]:
        out = (NAND(xs[0], xs[1]))
        print(str(xs) + " -> " + str(out))
        
    print()
    print("OR")
    for xs in [(0, 0), (1, 0), (0, 1), (1, 1)]:
        out = (OR(xs[0], xs[1]))
        print(str(xs) + " -> " + str(out))
        
    print()
    print("XOR")
    for xs in [(0, 0), (1, 0), (0, 1), (1, 1)]:
        out = (NAND(xs[0], xs[1]))
        print(str(xs) + " -> " + str(out))
        
<感想>
今回は基本的な内容が中心であり
難しいことは特になかった。
レポートの問題も簡単だったため、
突っかかることなく終えられてよかった。

<参考文献>
教材: 第２章 パーセプトロン
