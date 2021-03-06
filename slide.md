# Ammo Study Group
## 2018/05/28
Written by [Yuasa]().

---

# Chapter2
NumPy, SciPy, Pandas, Matpolot

---

# ```NumPy```

<<<

### ```NumPyとは```

NumPyとは、プログラミング言語Pythonにおいて数値計算を効率的に行うための拡張モジュール。効率的な数値計算を行うための多次元配列（ベクトルや行列など）をサポート。NumPyの内部はC言語によって実装されているため非常に高速に動作。[引用：Wikipedia](https://ja.wikipedia.org/wiki/NumPy)

<<<

### モジュール読み込み
```python
# numpyモジュールの読み込み
import numpy as np

# 小数第３まで表示という意味
%precision 3
```
<<<

### 配列の作成
```Python
# 配列の作成
sample_numpy_data = np.array([9,2,3,4,10,6,7,8,1,5])
sample_numpy_data
```
```Python
array([ 9,  2,  3,  4, 10,  6,  7,  8,  1,  5])
```
<<<

### データの型
```Python
# データの型
sample_numpy_data.dtype
```
```Python
dtype('int64')
```
<<<
>[ポイント]
>作業（コーディング）を早く正確にするためには、タブ[tab]を使いなそう

<<<
### 次元数、要素数の確認
```python
# 配列作成
sample_numpy_data = np.array([9,2,3,4,10,6,7,8,1,5])
# 次元数
print("次元数:",sample_numpy_data.ndim)						
# 要素数
print("要素数:",sample_numpy_data.size)
```
```python
次元数: 1
要素数: 10
```
<<<
### 配列の整数倍
```python
# 配列作成
sample_numpy_data = np.array([9,2,3,4,10,6,7,8,1,5])							
# それぞれの数字を係数倍（ここでは2倍）
sample_numpy_data * 2						
array([18,  4,  6,  8, 20, 12, 14, 16,  2, 10])
```

<<<

### 掛け算割り算
```python
# それぞれの要素同士での演算
print("掛け算:",np.array([1,2,3,4,5,6,7,8,9,10]) * np.array([10,9,8,7,6,5,4,3,2,1]))
print("累乗:",np.array([1,2,3,4,5,6,7,8,9,10]) **2)
print("割り算:",np.array([1,2,3,4,5,6,7,8,9,10]) / np.array([10,9,8,7,6,5,4,3,2,1]))
```
```python
掛け算: [10 18 24 28 30 30 28 24 18 10]
累乗: [  1   4   9  16  25  36  49  64  81 100]
割り算: [  0.1     0.222   0.375   0.571   0.833   1.2     1.75    2.667   4.5    10.   ]
```
<<<

### 初期化データ
```python							
# 0 や 1の初期化データ
# (2,3)は2行3列の行列データを作っています。
zero_data = np.zeros((2,3), dtype='i')
one_data = np.ones((2,3), dtype='f')
print("・0でint型　\n", zero_data)
print("・1でfloat型 \n", one_data)
```
```python							
・0でint型　
 [[0 0 0]
 [0 0 0]]
・1でfloat型
 [[1. 1. 1.]
 [1. 1. 1.]]
```
<<<

### ソート
```python
# 配列作成
sample_numpy_data = np.array([9,2,3,4,10,6,7,8,1,5])							
# そのまま							
print("そのまま：",sample_numpy_data)
# ソート
sample_numpy_data.sort()
print("ソート後：",sample_numpy_data)
```
```python
そのまま： [ 9  2  3  4 10  6  7  8  1  5]
ソート後： [ 1  2  3  4  5  6  7  8  9 10]
```

<<<
### 最小、最大、合計、積み上げ
```python
# 最小値
print("Min:",sample_numpy_data.min())
# 最大値
print("Max:",sample_numpy_data.max())
# 合計
print("Sum:",sample_numpy_data.sum())
# 積み上げ
print("Cum:",sample_numpy_data.cumsum())
# 積み上げ割合
print("Ratio:",sample_numpy_data.cumsum()/sample_numpy_data.sum())
```
```python
Min: 1
Max: 10
Sum: 55
Cum: [ 1  3  6 10 15 21 28 36 45 55]
Ratio: [0.018 0.055 0.109 0.182 0.273 0.382 0.509 0.655 0.818 1.   ]
```
<<<

### 乱数
```python
# 乱数の発生のためのモジュール読み込み
import numpy.random as random

# seedを設定することで乱数を固定化することができる
# これを設定しないと、テストなどでチェックするときに再現が困難になる
random.seed(0)

# 正規分布（平均0、分散1）の乱数を10個発生
norm_random_sample_data = random.randn(10)

print("乱数10個の配列:", norm_random_sample_data)
```
```python
乱数10個の配列: [ 1.764  0.4    0.979  2.241  1.868 -0.977  0.95  -0.151 -0.103  0.411]
```
<<<

### ランダム抽出
```python
# 乱数の発生のためのモジュール読み込み
import numpy.random as random

# ランダム抽出 配列の中からランダムに数値を抽出
print(random.choice(norm_random_sample_data,10))# 10個を抽出（重複あり,復元抽出） replace = True
print(random.choice(norm_random_sample_data,10,replace=False)) # 10個を抽出（重複なし、非復元抽出)
```
```python							
[-0.331 -0.423 -0.252 -0.363 -1.665 -0.363 -0.106 -0.331  0.712 -0.857]
[-0.331 -1.193  1.857  0.11   0.712 -0.252  0.996 -0.872 -0.106 -0.363]
```
<<<
### [やってみよう]
seed(0)の0を変えたり、ランダム抽出の数を増やしてみる。
```python
import numpy.random as random
i = 5 # Seed(i)
n = 10 #
random.seed(i)
norm_random_sample_data = random.randn(n)	# 正規分布（平均0、分散1）の乱数をn個発生
print( 'Seed(%d)乱数%d個の配列:%s'  % ( i, n, norm_random_sample_data ) )
```
```python
Seed(5)乱数10個の配列:[ 0.44122749 -0.33087015  2.43077119 -0.25209213  0.10960984  1.58248112
-0.9092324  -0.59163666  0.18760323 -0.32986996]
```							
<<<
### 処理速度
```python
# Nは乱数の発生数、10の6乗
N = 10**6
# normal version (以下のrange(N)は0からN-1までの整数を用意しています。 _ はあとで変数として使用しないため、このように表現します。)
normal_sample_data = [random.random() for _ in range(N)]
# numpy version
numpy_random_data = np.array(normal_sample_data)

# calc time :合計値
%timeit sum(normal_sample_data)
%timeit np.sum(numpy_random_data)
print(sum(normal_sample_data))
print(np.sum(normal_sample_data))
```
```python
5.65 ms ± 179 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
47 µs ± 12.3 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
500433.66103081836
500433.66103081347
```
<<<

>[ポイント]
>パフォーマンス等をあげたい場合は、```%timeit``` を使いながら、計算時間をチェックしましょう。

<<<
### 行列要素の抽出
```python
# データの準備
sample_multi_array_data1 = np.arange(9).reshape(3,3)
print(sample_multi_array_data1)
```
```python
[[0 1 2]
 [3 4 5]
 [6 7 8]]
```
```python
# 行 抽出
sample_multi_array_data1[0,:]
```
```python
array([0, 1, 2])
```
```python
# 列 抽出
sample_multi_array_data1[:,0]
```
```python
array([0, 3, 6])
```
<<<
### 行列の積
```python
# 行列の積 データの準備
sample_multi_array_data2 = np.arange(9,18).reshape(3,3)
print(sample_multi_array_data2)
```
```python
[[ 9 10 11]
[12 13 14]
[15 16 17]]
```
```python
# 行列の積（要素の積*ではない）
np.dot(sample_multi_array_data1,sample_multi_array_data2)
```
```python
array([[ 42,  45,  48],
       [150, 162, 174],
       [258, 279, 300]])
```							
<<<
### <練習問題 1>
1から50までの自然数の和を計算するプログラムを書いて、最後の計算結果を表示させるプログラムを書いてください。ただし、Numpyを使ってください。
<<<
```python
import numpy as np
sample_data = np.ones([50],dtype='i')
#print(sample_data)
#print(sample_data.cumsum())
print(sample_data.cumsum().sum())
```
```
1275
```
<<<																												
### <練習問題 2>
正規分布に従う乱数を10個発生させて配列を作成してください。また、その中での最小値、最大値、合計を求めるプログラムを書いてください。
```python
import numpy.random as random
i = 30
n = 100000
random.seed(i)
# 正規分布（平均0、分散1）の乱数をn個発生
norm_random_sample_data = random.randn(n)
print('最大は', norm_random_sample_data.max())
print('最小は', norm_random_sample_data.min())
print('合計は', norm_random_sample_data.sum())
```
```
最大は 4.332650493583902
最小は -4.529364871884005
合計は -356.39499767757576
```
<<<
### <練習問題 3>
要素がすべて3の5行5列の行列を作成し、その行列の2乗をする計算をしてみましょう。
<<<
```python
three_mat = 3*np.ones([5,5],dtype='i')
print(three_mat **2)
```
```python
[[9 9 9 9 9]
 [9 9 9 9 9]
 [9 9 9 9 9]
 [9 9 9 9 9]
 [9 9 9 9 9]]
```
---

# ```SciPy```

<<<

### ```SciPyとは```
数値計算用ライブラリ。MatLabとかMathmaticaを代替しよう！って作られたもの。統計、最適化、積分、線形代数、フーリエ変換、信号・イメージ処理、遺伝的アルゴリズム、ODE (常微分方程式) ソルバを提供する。[引用1：Wikipedia](https://ja.wikipedia.org/wiki/NumPy)、[引用2：SciPyとその仲間たち](http://d.hatena.ne.jp/over80/20160221/scipy)

<<<
### モジュールのインポート
```python
# Scipyのモジュール
import scipy as sp

# 線形代数用のモジュール
import scipy.linalg as linalg
# linear algebra

# 最適化計算（最小値）用のモジュール
from scipy.optimize import minimize_scalar
```

<<<
### 行列式
```python
# サンプルデータ作成
sample_matrix_data = np.array([[1,-1,-1],[-1,1,-1],[-1,-1,1]])
```
```python
# 行列式 Determinant
print(sample_matrix_data)
print("行列式")
print(linalg.det(sample_matrix_data))
```
```python
[[ 1 -1 -1]
 [-1  1 -1]
 [-1 -1  1]]
行列式
-4.0
```
<<<

### 逆行列
```python
# 逆行列
print("逆行列")
print(linalg.inv(sample_matrix_data))
```
```python
逆行列
[[ 0.  -0.5 -0.5]
 [-0.5 -0.  -0.5]
 [-0.5 -0.5  0. ]]
```
```python
# 確認
print(sample_matrix_data.dot(linalg.inv(sample_matrix_data)))
	```
```python
[[ 1.  0.  0.]
	[ 0.  1.  0.]
  [ 0.  0.  1.]]
```

<<<

### 固有値、固有ベクトル
```python
# 固有値と固有ベクトル　eigenvalue

eig_value, eig_vector = linalg.eig(sample_matrix_data)

# 固有値と固有ベクトル
print("固有値")
print(eig_value)
print("固有ベクトル")
print(eig_vector)
```
```python
固有値
[-1.+0.j  2.+0.j  2.+0.j]
固有ベクトル
[[ 0.577 -0.816  0.428]
 [ 0.577  0.408 -0.816]
 [ 0.577  0.408  0.389]]							
	```
<<<
### 最適化計算 数値解析
```python
# 関数の定義
def sample_function(x):
    return (x**2 + 2*x + 1)
```
```python
# ニュートン法の読み込み
from scipy.optimize import newton

# 計算実行
print(newton(sample_function,0))
```
```
-0.9999999852953547
```
<<<
### ニュートン法に関する参考文献
 [参考URL]
 https://ja.wikipedia.org/wiki/ニュートン法
 http://qiita.com/PlanetMeron/items/09d7eb204868e1a49f49
<<<
### <練習問題 1>
以下の行列について、行列式を求めてください。
```python
# 線形代数用のモジュール
import scipy.linalg as linalg
A = np.array([[1,2,3],[1,3,2],[3,1,2]])
print('行列：\n', A)
print('行列式：', linalg.det(A))
```
```Python
行列：
 [[1 2 3]
 [1 3 2]
 [3 1 2]]
行列式： -12.000000000000002
```
<<<
### <練習問題 2>
上と同じ行列について、逆行列、固有値と固有ベクトルを求めてください。
```python
# 逆行列
print("逆行列\n",linalg.inv(A))
# 固有値と固有ベクトル　eigenvalue
eig_value, eig_vector = linalg.eig(A)
# 固有値と固有ベクトル
print("固有値¥n",eig_value)
print("固有ベクトル¥n",eig_vector)
```
```Python
逆行列
[[-0.333  0.083  0.417]
 [-0.333  0.583 -0.083]
 [ 0.667 -0.417 -0.083]]
固有値
[ 6.   +0.j -1.414+0.j  1.414+0.j]
固有ベクトル
[[-0.577 -0.722  0.16 ]
 [-0.577 -0.143 -0.811]
 [-0.577  0.677  0.563]]
```
<<<
<練習問題 3>
以下の関数が0となる解を求めてみましょう
```python
# ニュートン法の読み込み
from scipy.optimize import newton

# 関数の定義
def sample_function(x):
    return (x**3 + 2*x + 1)

# 計算実行 sample_fucntion(x) =　 0
print(newton(sample_function,0))							
```
```
-0.4533976515164037
```
---

# ```Pandas```

<<<

### ```Pandasとは```
データ解析を支援する機能を提供するライブラリ。数表および時系列データを操作するためのデータ構造と演算を提供。
キーワード：Series、DataFrame、データの操作、データの結合、ソート。
[引用1：Wikipedia](https://ja.wikipedia.org/wiki/Pandas)

<<<
### モジュール読み込み
```python
from pandas import Series,DataFrame
import pandas as pd
```

※fromを使うことで、クラスを直接呼び出すことができモジュール名を記述する必要がなくなる。

<<<
### ```Series```
```python
# Series 配列のようなオブジェクト
sample_pandas_data = pd.Series([0,1,2,3,4,5,6,7,8,9])
print(sample_pandas_data)
```
```python
0    0
1    1
2    2
3    3
4    4
5    5
6    6
7    7
8    8
9    9
dtype: int64
```
```python
print("データの値:",sample_pandas_data.values)
print("インデックスの値:",sample_pandas_data.index)
```
```python
データの値: [0 1 2 3 4 5 6 7 8 9]
インデックスの値: RangeIndex(start=0, stop=10, step=1)
```

<<<
### インデックスの操作							
```python
# indexを文字で
sample_pandas_index_data = pd.Series([0,1,2,3,4,5,6,7,8,9]
                                     ,index=['a','b','c','d','e','f','g','h','i','j'])
print(sample_pandas_index_data)
```
```python
a    0
b    1
c    2
d    3
e    4
f    5
g    6
h    7
i    8
j    9
dtype: int64
```
```python
print("データの値:",sample_pandas_index_data.values)
print("インデックスの値:",sample_pandas_index_data.index)
```
```python
データの値: [0 1 2 3 4 5 6 7 8 9]
インデックスの値: Index(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'], dtype='object')
```

<<<

### ```DataFrame```
※ 各々の列で異なる型を持たせることが可能
```python
attri_data1 = {'ID':['100','101','102','103','104']
        ,'city':['Tokyo','Osaka','Kyoto','Hokkaidao','Tokyo']
        ,'birth_year':[1990,1989,1992,1997,1982]
        ,'name':['Hiroshi','Akiko','Yuki','Satoru','Steeve']}
# 辞書型 mydic = {'key1':val1,'key2':val2}				
attri_data_frame1 = DataFrame(attri_data1) #pd.DataFrameの略
print(attri_data_frame1)
```
```
ID  birth_year       city     name
0  100        1990      Tokyo  Hiroshi
1  101        1989      Osaka    Akiko
2  102        1992      Kyoto     Yuki
3  103        1997  Hokkaidao   Satoru
4  104        1982      Tokyo   Steeve
```

<<<

### ```DataFrame```のインデックスの更新
```python
attri_data_frame_index1 = DataFrame(attri_data1,index=['a','b','c','d','e'])
print(attri_data_frame_index1)
```
```
ID  birth_year       city     name
a  100        1990      Tokyo  Hiroshi
b  101        1989      Osaka    Akiko
c  102        1992      Kyoto     Yuki
d  103        1997  Hokkaidao   Satoru
e  104        1982      Tokyo   Steeve
```

<<<

### ```DataFrame```による転置
```python
attri_data_frame1.T # DataFrameクラスのメソッドT
```
```
0	1	2	3	4
ID	100	101	102	103	104
birth_year	1990	1989	1992	1997	1982
city	Tokyo	Osaka	Kyoto	Hokkaidao	Tokyo
name	Hiroshi	Akiko	Yuki	Satoru	Steeve
```

<<<
### カラム（列）
![](https://academy.gmocloud.com/wp/wp-content/uploads/2016/04/160425_DBword_04.png)

<<<

### カラム（列）を指定して抽出```DataFrame```
```python
# 列名の指定（１つ）
attri_data_frame1.birth_year
```
```
0    1990
1    1989
2    1992
3    1997
4    1982
Name: birth_year, dtype: int64
```

<<<

### 複数カラム（列）を指定して抽出```DataFrame```
```python
# 列名の指定(複数の場合)
attri_data_frame1[["ID","birth_year"]]
```
```
ID	birth_year
0	100	1990
1	101	1989
2	102	1992
3	103	1997
4	104	1982
```

<<<

### フィルタ：条件を指定してデータ抽出```DataFrame```
```python
#　条件（フィルター）　CityがTokyoである要素を抽出
attri_data_frame1[attri_data_frame1['city']=='Tokyo']
```
```
ID	birth_year	city	name
0	100	1990	Tokyo	Hiroshi
4	104	1982	Tokyo	Steeve
```
```python
#　条件（フィルター、複数の値）
attri_data_frame1[attri_data_frame1['city'].isin(['Tokyo','Osaka'])]
```
```
ID	birth_year	city	name
0	100	1990	Tokyo	Hiroshi
1	101	1989	Osaka	Akiko
4	104	1982	Tokyo	Steeve
```

<<<
### [やってみよう]
他にも条件を変更（birth_yearが1990未満など）して、フィルターを実行してみましょう。
```python
attri_data_frame1[attri_data_frame1['city']<1900]
```
```
ID	birth_year	city	name
1	101	1989	Osaka	Akiko
4	104	1982	Tokyo	Steeve
```
この入れ子関係覚えられん

<<<

### 特定の列の削除```DataFrame```
axisで軸を設定し、1の場合は列方向。行の削除はインデックスを指定して、axis=0。
```python
# データの列の削除
attri_data_frame1.drop(['birth_year'],axis=1)
```
```
ID	city	name
0	100	Tokyo	Hiroshi
1	101	Osaka	Akiko
2	102	Kyoto	Yuki
3	103	Hokkaidao	Satoru
4	104	Tokyo	Steeve
```

<<<
### テーブルの結合```DataFrame```
```python
# 別のデータの準備
attri_data2 = {'ID':['100','101','102','105','107']
        ,'math':[50,43,33,76,98]
        ,'English':[90,30,20,50,30]
        ,'sex':['M','F','F','M','M']}
attri_data_frame2 = DataFrame(attri_data2)
```
```
English   ID  math sex
0       90  100    50   M
1       30  101    43   F
2       20  102    33   F
3       50  105    76   M
4       30  107    98   M
```

<<<

### テーブルの結合2```DataFrame```
```python
# データのマージ（内部結合、詳しくは次の章で）
pd.merge(attri_data_frame1,attri_data_frame2)
```
idが共通である100,101,102が結合される
```
ID	birth_year	city	name	English	math	sex
0	100	1990	Tokyo	Hiroshi	90	50	M
1	101	1989	Osaka	Akiko	30	43	F
2	102	1992	Kyoto	Yuki	20	33	F
```

<<<

### グループ集計```DataFrame```
``` python
# データのグループ集計(詳しくは次の章で)
attri_data_frame2.groupby("sex")["math"].mean()
```
```
sex
F    38.000000
M    74.666667
Name: math, dtype: float64
```
これも()[]とかよくわからん

<<<

### ```Pandas.DataFrame``` のソート機能
```Python
# データの準備
attri_data2 = {'ID':['100','101','102','103','104']
        ,'city':['Tokyo','Osaka','Kyoto','Hokkaido','Tokyo']
        ,'birth_year':[1990,1989,1992,1997,1982]
        ,'name':['Hiroshi','Akiko','Yuki','Satoru','Steeve']}
attri_data_frame2 = DataFrame(attri_data2)
attri_data_frame_index2 = DataFrame(attri_data2,index=['e','b','a','d','c'])
print(attri_data_frame_index2)
```
```
ID  birth_year      city     name
e  100        1990     Tokyo  Hiroshi
b  101        1989     Osaka    Akiko
a  102        1992     Kyoto     Yuki
d  103        1997  Hokkaido   Satoru
c  104        1982     Tokyo   Steeve
```
<<<

### ```Pandas.DataFrame``` のソート機能2
```python
# indexによるソート
attri_data_frame_index2.sort_index()
```
```
ID	birth_year	city	name
a	102	1992	Kyoto	Yuki
b	101	1989	Osaka	Akiko
c	104	1982	Tokyo	Steeve
d	103	1997	Hokkaido	Satoru
e	100	1990	Tokyo	Hiroshi
```

<<<

# 値によるソート、デフォルトは昇順
attri_data_frame_index2.birth_year.sort_values()

c    1982
b    1989
e    1990
a    1992
d    1997
Name: birth_year, dtype: int64

<<<

最後に、値があるかどうか、Nullの判定についてです。

以下は、attri_data_frame_index2にTokyoという文字列があるかどうかをisinで調べて、それぞれのセルにTrueかFalseが返されます。入っていればTrue、入っていなければFalseになっていることがわかります。
# 値があるかどうかの確認
attri_data_frame_index2.isin(["Tokyo"])

ID	birth_year	city	name
e	False	False	True	False
b	False	False	False	False
a	False	False	False	False
d	False	False	False	False
c	False	False	True	False

---

### このスライドは **[reveal.js](https://github.com/hakimel/reveal.js/)** で作成！
<br>
- Markdown記法でのスライド作成ツール
- いい感じのスライドをパパッと作成可能
