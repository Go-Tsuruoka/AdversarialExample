# AdversarialExample
Adversarial Exampleの有名手法(FGSMなど)について、PyTorchで実装をしたもの。
攻撃対象はMNISTデータセットの数字を分類するモデルである。重みの取得方法やモデルの詳細、詳しい攻撃方法についてはnotebookに記載されているためここでは割愛する。

# コード内容
## FGSM.ipynb

FGSM攻撃の論文実装
FGSM攻撃は、ロスを最大化させる方向に対して、入力にノイズを加える。これにより、予測を誤らせることを狙う。
この攻撃は、予測を誤らせる手法であり、特定の出力になるようにノイズを加えるものではない。(ターゲットを決めることもできるが割愛。)

## JSMA.ipynb
Jacobian Saliency Map Attackを実装したもの。
この攻撃は、出力に対する入力の勾配をもとに、ノイズを加えるもの。ターゲットを定めて攻撃することができる。(2に誤検知するといったノイズの付与を行う。)

## CandW.ipynb
C&W攻撃の論文を実装したもの。
出力値に注目して、攻撃を行うもの。元画像との差異を小さくしつつ、ターゲットの出力が最大化されるように最適化問題を解くことで画像を生成する。

## my_attack_model.ipynb
自作の畳み込みオートエンコーダーを作って、ノイズを加えてみたもの。具体的には、誤判定させたいターゲットを定めて、それに対するロスがすくなるようにする。このとき、ノイズのL1ノルムも考慮する。

# 出力例
## FGSM
![FGSM_output](https://user-images.githubusercontent.com/64346532/236625752-f969394c-2730-4969-9a6d-504289a12466.png)
## JSMA
6が2に誤判定されたときの出力

![JSMA_output](https://user-images.githubusercontent.com/64346532/236626091-dc2b6212-3ad9-48c9-b420-28a10ede6f70.png)

## C&W
0が1に誤判定されたときの出力

![output_CandW](https://user-images.githubusercontent.com/64346532/236625945-63b478bd-3721-4443-ae70-a3a3fe095394.png)

## 自作モデル
0が1と誤判定されたときの出力

![mymodel_before](https://user-images.githubusercontent.com/64346532/236626025-36f828ff-7676-4e71-8e65-3330600efa6c.png)

![mymodel_after](https://user-images.githubusercontent.com/64346532/236626060-7a1827c2-9c2e-432f-a16b-82ffc531cbf6.png)





