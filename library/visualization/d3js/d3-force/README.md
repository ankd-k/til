# d3-force

[Github](https://github.com/d3/d3-force)

---

## 概要

物理シミュレーションを実装したモジュール。
d3じゃなくても使える。

---

## 使い方

1. インスタンス生成
2. 各種シミュレーション設定をメソッドチェーンで追加する
3. アニメーションなり一発なり好きな方法でシミュレーションを走らせる

---

## Force設定

### [Centering](https://github.com/d3/d3-force#centering)

中心指定

### [Collision](https://github.com/d3/d3-force#collision)

ノードを点ではなく半径があるものとして、重なるのを防ぐ。

### [Links](https://github.com/d3/d3-force#links)

目的の距離に応じてばねのように押し合ったり引き合ったりさせる。

### [Many-Body](https://github.com/d3/d3-force#many-body)

ノード全体の重力（ノード同士が引き合う）・斥力（ノード同士が反発しあう）。  
strengthが正なら重力、負なら斥力。  
全体を散らすのに使える。

### [Positioning](https://github.com/d3/d3-force#positioning)

指定した位置に強制する。
