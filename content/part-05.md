# 21. 測度論から見た確率・条件付き期待値

## 21.1 ルベーグ積分による統一

有限標本空間ならすべての部分集合を事象として扱えるが、連続空間では可測集合に確率を定義する。実数上のBorel集合族は開集合から生成される $\sigma$-加法族。確率変数の可測性とは、任意のBorel集合 $B$ に対して $X^{-1}(B)\in\mathcal F$ であることをいう。

期待値はルベーグ積分 $E[X]=\int_\Omega X(\omega)dP(\omega)$ として統一的に定義する。非負単関数 $s=\sum_j a_j\mathbf1_{A_j}$（排反な $A_j$）なら $\int s\,dP=\sum_j a_jP(A_j)$。一般の非負可測関数へは下から近似する単関数の積分の上限で拡張する。符号付き可積分関数は正部分と負部分の積分の差で定義する。

分布 $P_X(B)=P(X^{-1}(B))$ を像測度と呼ぶ。積分の変数を確率変数の値の空間へ移すと

$$
E[g(X)]=\int_{\mathbb R}g(x)dP_X(x).
$$

これが離散型の和と連続密度型の積分を統一する式である。

## 21.2 条件付き期待値の一般的な定義

$Y$ を可積分、$\mathcal G\subset\mathcal F$ を部分 $\sigma$-加法族とする。$E[Y\mid\mathcal G]$ は $\mathcal G$ 可測な可積分確率変数 $Z$ で、任意の $A\in\mathcal G$ について

$$
\int_A Z\,dP=\int_A Y\,dP
$$

を満たすものとして定義される。Radon–Nikodymの定理に基づき存在し、ほとんど確実に一意である。$\mathcal G$ は利用できる情報を表し、$Z$ はその情報で説明できる平均と解釈できる。$E[Y\mid X]$ は $E[Y\mid\sigma(X)]$ の略記である。

二乗可積分なら条件付き期待値は $L^2(\mathcal G)$ への直交射影であり、$E[(Y-Z)W]=0$ が任意の $\mathcal G$ 可測な二乗可積分変数 $W$ について成立する。最小二乗予測の一般的な根拠となる。

## 21.3 収束概念と積分の交換

| 収束 | 定義の要点 |
|:---|:---|
| ほとんど確実収束 | $P(\lim X_n=X)=1$ |
| 確率収束 | $P(|X_n-X|>\epsilon)\to0$（全 $\epsilon>0$） |
| $L^p$ 収束 | $E[|X_n-X|^p]\to0$（$p\ge1$） |
| 分布収束 | CDFが極限CDFの連続点で収束 |

ほとんど確実収束または $L^p$ 収束から確率収束が従い、確率収束から分布収束が従う。逆は一般に成立しない。$0\le X_n\uparrow X$ なら単調収束定理、$X_n\to X$ a.s. かつ $|X_n|\le Y$、$E[Y]<\infty$ なら優収束定理によって期待値と極限を交換できる。

## 演習 21

$U\sim U(0,1)$ とし $X_n=n\mathbf1_{\{U<1/n\}}$ と置く。ほとんど確実収束先と期待値の極限を求めよ。

**解答.** $U>0$ なら十分大きな $n$ で0なので a.s. に0へ収束。一方 $E[X_n]=n/n=1$ なので期待値は0へ収束しない。収束だけでは積分と極限を交換できない。

# 22. 数理統計の発展：十分統計量・情報量・漸近理論

## 22.1 十分統計量と指数型分布族

十分統計量 $T(X)$ とは、母数について標本が持つ情報を損なわない要約である。共通の支配測度を持つモデルで因子分解定理を使うと、同時密度が

$$
f_\theta(\mathbf x)=g_\theta(T(\mathbf x))h(\mathbf x)
$$

と分解できれば $T$ は十分統計量である。Bernoulli標本では尤度が $p^{\sum x_i}(1-p)^{n-\sum x_i}$ なので、成功回数 $T=\sum_iX_i$ に集約してよい。どの順番で成功したかは、i.i.d. Bernoulliモデルでは母数 $p$ の追加情報を持たない。時系列依存があればこの議論は変わる。

指数型分布族は $f_\theta(x)=h(x)\exp(\eta(\theta)^TT(x)-A(\theta))$ という形を持つ。正規化項 $A$ は積分を1にする。自然母数 $\eta$ で表し微分と積分を交換できれば、$\nabla A(\eta)=E_\eta[T(X)]$、Hessianは $T$ の共分散行列となる。

## 22.2 Cramér–Rao下限の導出

正則な1次元母数モデルを考える。全標本のスコアを $U=\partial_\theta\log f_\theta(\mathbf X)$ とすると、密度の積分1を微分して $E_\theta[U]=0$。不偏推定量 $T$ について $E_\theta[T]=\theta$ を微分すると $E_\theta[TU]=1$。従って $\operatorname{Cov}(T,U)=1$ である。Cauchy–Schwarz不等式より

$$
1\le\operatorname{Var}(T)\operatorname{Var}(U)
=\operatorname{Var}(T)nI(\theta).
$$

ゆえに第11章の下限が得られる。微分と積分の交換、母数に依存しない台などの正則条件が重要である。十分統計量で不偏推定量を条件付けすると分散が減少するRao–Blackwellの定理も、全分散の公式から理解できる。

## 22.3 最尤推定量の漸近正規性

識別可能性・内点の真値・十分な滑らかさ・一致性・非退化な情報量などの条件の下で、1次元MLEは

$$
\sqrt n(\hat\theta_n-\theta_0)\xrightarrow{d}N(0,I(\theta_0)^{-1}).
$$

証明の概略：スコアの方程式を真値の近傍でTaylor展開すると

$$
0=\ell_n'(\hat\theta_n)=\ell_n'(\theta_0)+\ell_n''(\tilde\theta_n)(\hat\theta_n-\theta_0).
$$

整理して $\sqrt n(\hat\theta_n-\theta_0)=-[\ell_n''(\tilde\theta_n)/n]^{-1}[\ell_n'(\theta_0)/\sqrt n]$。適切な一様収束条件の下で分母側は $-I(\theta_0)$ に確率収束し、分子側はCLTで $N(0,I(\theta_0))$ に分布収束する。Slutskyの定理から結論を得る。これは一般定理の完全な証明ではなく、構造を示したものである。

Delta法：$\sqrt n(\hat\theta-\theta)\to_d N(0,V)$、$g$ が $\theta$ で微分可能なら $\sqrt n(g(\hat\theta)-g(\theta))\to_d N(0,g'(\theta)^2V)$。一次Taylor展開で、変換後の推定量の標準誤差を近似できる。

## 22.4 KL情報量・モデル選択

密度 $p,q$ のKullback–Leibler情報量は

$$
D_{\mathrm{KL}}(p\|q)=E_p\left[\log\frac{p(X)}{q(X)}\right]\ge0.
$$

分布の違いを対数密度比で測るが、対称性はない。真の分布が $p$ のとき、期待対数尤度を最大化することは $D_{\mathrm{KL}}(p\|q_\theta)$ を最小化することと同じ。AICは $-2\ell(\hat\theta)+2k$、BICは $-2\ell(\hat\theta)+k\log n$（$k$ は自由母数数）。両方とも小さい方を選ぶが、AICは予測的な適合を、BICは一定条件でモデル同定を重視する考え方と結び付く。同じデータ・比較可能な尤度で使用する。

## 演習 22

Bernoulliの標本比率 $\hat p$ に対し、$g(p)=\log[p/(1-p)]$ の漸近分散をDelta法で求めよ（$0<p<1$）。

**解答.** $g'(p)=1/[p(1-p)]$、$\sqrt n(\hat p-p)$ の極限分散は $p(1-p)$。従って変換後の $\sqrt n$ スケールの分散は $1/[p(1-p)]$、推定量自身の近似分散は $1/[np(1-p)]$。全成功または全失敗の有限標本ではlogitが有限でない点に注意する。

# 付録 A. 公式を選ぶための整理

| 知りたいこと | 使う道具 | 確認する前提 |
|:---|:---|:---|
| 発生回数 | 二項・ポアソン | 独立性、率、過分散 |
| 発生までの時間 | 幾何・指数・ガンマ | 離散か連続か、発生率 |
| 標本平均の変動 | 標準誤差・CLT | 独立性、有限分散 |
| 母数の推定 | 最尤法・モーメント法 | モデルの識別可能性 |
| 平均の不確実性 | $t$ 信頼区間 | 独立正規標本等 |
| 差の検証 | 対応検定・Welch検定 | 対応、依存、検出力 |
| 二値応答 | ロジスティック回帰 | 条件付き平均、分離 |
| 将来の観測 | 予測区間 | 時間依存、母数の不確実性 |
| モデルの選択 | 検証誤差・AIC等 | 比較条件、データ漏洩 |

よく混同される点：確率と密度、相関と独立、標準偏差と標準誤差、尤度と母数の分布、信頼区間と予測区間、非棄却と同等性、統計的有意差と実務上の重要性。これらを区別できることが公式を覚えること以上に重要である。

# 付録 B. Pythonで理論を確認する

以下は NumPy、SciPy、Matplotlib を用いる独立した実験である。乱数のシードを固定しているが、ライブラリのバージョンによって細部が変わる場合がある。コード内のデータはすべて人工データ。

## B.1 中心極限定理：元の分布と標本平均の違い

指数分布は右に歪むが、標本平均を標準化すると標準正規分布に近づく。標本サイズを変えて確認する。

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

rng = np.random.default_rng(42)
n, B = 30, 10000
x = rng.exponential(scale=1, size=(B, n))
z = np.sqrt(n) * (x.mean(axis=1) - 1)
grid = np.linspace(-4, 4, 200)
plt.hist(z, bins=60, density=True, alpha=0.6)
plt.plot(grid, stats.norm.pdf(grid))
plt.xlabel('Standardized sample mean')
plt.show()
print(z.mean(), z.std(ddof=1))
```

観察点：平均は0、標準偏差は1に近づく。$n=1,5,30,100$ を比較し、右への歪みがどのように変化するかを見る。

## B.2 Bernoulli最尤推定とWilson区間

```python
import numpy as np
from scipy import stats

k, n = 12, 100
p_hat = k / n
z = stats.norm.ppf(0.975)
center = (p_hat + z*z/(2*n)) / (1 + z*z/n)
half = z*np.sqrt(p_hat*(1-p_hat)/n + z*z/(4*n*n))
half /= (1 + z*z/n)
print(p_hat, (center-half, center+half))
```

観察点：$k=0,1,50,100$ と変え、Wilson区間の非対称性や端点付近の挙動を確認する。

## B.3 信頼区間の被覆率

```python
import numpy as np
from scipy import stats

rng = np.random.default_rng(42)
mu, sigma, n, B = 40, 10, 25, 10000
x = rng.normal(mu, sigma, size=(B, n))
m, s = x.mean(axis=1), x.std(axis=1, ddof=1)
h = stats.t.ppf(0.975, n-1)*s/np.sqrt(n)
coverage = np.mean((m-h <= mu) & (mu <= m+h))
print(coverage)
```

観察点：95%に近い被覆率が得られるかを確認する。個々の区間に真値が入るかどうかは0か1だが、多数の反復で約95%という性質が現れる。

## B.4 最小二乗とブートストラップ

```python
import numpy as np

rng = np.random.default_rng(42)
x = np.array([10., 20., 30., 40., 50.])
y = np.array([15., 25., 32., 39., 52.])
X = np.column_stack([np.ones(len(x)), x])
beta, *_ = np.linalg.lstsq(X, y, rcond=None)
print('OLS:', beta)
# Independent bootstrap of the sample mean
B = 5000
resamples = rng.choice(y, size=(B, len(y)), replace=True)
means = resamples.mean(axis=1)
print('SE:', means.std(ddof=1))
print('CI:', np.quantile(means, [0.025, 0.975]))
```

観察点：この再標本化は平均の変動を説明するものであり、回帰係数の区間を計算しているわけではない。標本サイズ5では百分位区間の被覆率が正確とは限らない。

## B.5 ローリング予測の最小構成

```python
import numpy as np

rng = np.random.default_rng(42)
y = 20 + rng.normal(0, 3, 150)
errors = []
for t in range(60, len(y)):
    train = y[:t]  # only data before target t
    pred = train[-30:].mean()
    errors.append(y[t] - pred)
e = np.asarray(errors)
print('MAE:', np.mean(np.abs(e)))
print('RMSE:', np.sqrt(np.mean(e**2)))
```

観察点：直近30日の平均という単純モデルで、予測時点より後の情報を用いず評価する。窓幅を複数比較するときは、検証期間と最終テスト期間を分離する。

# 付録 C. 4週間の学習計画

| 週 | 範囲 | 確認する課題 |
|:---|:---|:---|
| 1 | 1–8章 | 分布・期待値の計算、LLNの証明 |
| 2 | 9–15章 | 不偏分散、MLE、区間・検定の導出 |
| 3 | 16–20章 | OLS、PCA、再標本化、時系列評価 |
| 4 | 21–22章・付録 | 測度論、漸近正規性、研究データへの適用 |

各日、定義の確認、導出の再現、演習、Python実験の順に進める。すべての公式を暗記する必要はないが、なぜその形にするのかを自分の言葉で説明できるようにする。証明をさらに厳密に学ぶ場合は下記の専門講義へ進む。

