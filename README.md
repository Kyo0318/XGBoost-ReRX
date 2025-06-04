# XGBoost-Optuna Hybrid vs. Re-RX: 性能・解釈性比較研究

## 概要

本リポジトリは、心血管疾患（CVD）データに対する高精度かつ説明可能な機械学習モデルの構築と評価を目的としています。具体的には、以下の2モデルを実装・比較します：

- **Hybrid-XGBoost**：外れ値処理＋Optunaによるハイパーパラメータ最適化付きXGBoost
- **Re-RX with J48graft**：ニューラルネットワークからif-thenルールを抽出し構造化する手法

本研究では、両モデルの**性能指標**（Accuracy, F1など）と**解釈性指標**（ルール数、Fidelityなど）を体系的に比較し、「精度と解釈性のトレードオフ」を定量化することを目的としています。

---

## 使用データ

- Cleveland Heart Disease Dataset
- Heart Failure Clinical Records Dataset（Kaggle等で取得可能）

---

## データ前処理

- 欠損値補完（平均/中央値など）
- 外れ値処理：Z-スコア＋IQR法
- 特徴量スケーリング：Min-Max正規化

---

## モデル構築

### 1. Hybrid-XGBoost
- ライブラリ：`xgboost`, `optuna`, `scikit-learn`
- ハイパーパラメータ最適化：Optunaによるベイズ最適化
- 交差検証：StratifiedKFoldによるk-fold（例：5分割）

### 2. Re-RX (with J48graft)
- ニューラルネットワーク：`Keras` or `PyTorch`
- ルール抽出：Re-RXアルゴリズム（独自実装または参考文献に基づく）
- 決定木構造化：J48graft（`weka`ベース実装を参考）

---

## 評価指標

- 性能：Accuracy, Sensitivity, Specificity, Precision, F1
- 解釈性：ルール数、平均ルール長、Fidelity、Feature Coverage
- 統計検定：Friedman検定＋Dunn事後検定

---

## 実験設定

- 外れ値有無での比較
- 訓練/テスト分割：70:30, 80:20, 90:10
- 交差検証により統計的信頼性を確保

---

## 可視化・出力例

- 混同行列
- 重要特徴量（SHAP/Feature Importance）
- ルールのif-thenリスト

---

## 参考文献

- Tanaka, Y. "Re-RX with J48graft" (2022)
- Dhanka, S. & Maini, S. "Hybridization of XGBoost..." (2025)
- Srinivas, P. et al. "Hyper-tuned XGBoost with Optuna for CVD" (2022)
- Quinlan, J. R. “C4.5: Programs for Machine Learning” (1993)

---
