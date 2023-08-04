# サイトがインデックスされるかをDNNの二項分類で予測する
隠し層の数、ノード数、ドロップアウト率などのハイパーパラメータのチューニング（ハイパーチューニング）は、keras_tunerのBayesianOptimization（ベイズ最適化）を使用する。<br>
BayesianOptimizationは最適なハイパーパラメータを選択してモデルを作成してくれる。<br>
<br>

### 大まかな処理の流れ
1. データの取り込み
2. データの整形（トレーニングデータとテストデータを作成）
3. モデルの定義
4. チューナーをインスタンス化して、ハイパーパラメータのチューニングする
5. チューニングしたハイパーパラメータでモデルを作成し、トレーニングする
6. 作成したモデルを保存する
7. 保存したモデルを読み込み、予測したいデータで予測する
<br>

# ファイル構成
- 「index_model」フォルダ：作成したモデル情報が保存されている。
- 「index_predict」フォルダ：ハイパーチューニングの際のログなどが出力される。tensorBoardを使用する際はこのフォルダ配下のファイルが参照される。
- create_dnn_model_for_index_predict.ipynb：サイトがインデックスされるかを予測するモデルの作成を行う。
- dnn_binary_classification_of_heart_disease.ipynb：Keras公式ドキュメントの[サンプルコード](https://keras.io/examples/structured_data/structured_data_classification_with_feature_space/)をDNNに改良し、keras_tunerを使用してハイパーチューニングするように改良したコード
- index_data.json：サイトインデックス予測用のモックデータ
- index_predict.ipynb：作成したモデルを使用して、サイトがインデックスされるかを予測する。
- indexfeaturespace.keras：作成したフューチャースペース（インデックス予測に必要な為、出力している）
- README.md：本ファイル
<br>

# 環境構築
※前提条件として、Node.jsとPythonはインストールされているものとする。<br>
<br>
tensorflowをインストールする。<br>

```bash
pip install tensorflow
```
<br>

# 使用方法
実行したいファイルを開き、メニュー「Cell」タブ内の「Run All」を押下する。

- create_dnn_model_for_index_predict.ipynb：モデル作成に使用するデータに応じて、パラメーター等を変更してから実行すること。
- index_predict.ipynb：モデルが作成済み（create_dnn_model_for_index_predict.ipynbが実行済）であることが前提。予測したいデータを渡して、実行する。